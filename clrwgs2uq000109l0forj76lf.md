---
title: "Razorpay Payment Gateway Integration In Laravel"
seoTitle: "2024 -Razorpay Payment Gateway Integration in  Laravel 10"
datePublished: Sat Jan 27 2024 19:27:50 GMT+0000 (Coordinated Universal Time)
cuid: clrwgs2uq000109l0forj76lf
slug: razorpay-payment-gateway-integration-in-laravel
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706362102640/b758ea48-742f-4b6a-ab1b-945003d997af.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1706383389780/022c1bad-8916-4ea4-a76f-abd1d72c1339.png
tags: laravel, payment-gateway, razorpay, laraveldevelopment

---

# Razorpay Payment Gateway Integration In Laravel

In this tutorial, you will learn how to integrate RazorPay in your Laravel 10 application. Read on to know the essential steps for the integration. This article will cover the all the all the cases involved in the payment feature.

## **Steps to Integrate Razorpay Payment Gateway In Laravel**

The Step by Step process to implement this feature in Laravel 10 Application.

## **Step 1 - Install the Laravel 10 Application**

Install the laravel application directory where ever you want to using this command.

```bash
composer create-project laravel/laravel IntegrateRazorpayInLaravel
```

## **Step 2 - Connect Database to an Application**

Update the database configuration in `.env`

```yaml
DB_CONNECTION=mysql
DB_HOST=localhost
DB_PORT=3306
DB_DATABASE=razorpay
DB_USERNAME=root
DB_PASSWORD=
```

## **Step 3 - Add RazorPay Credentials From Dashboard**

Access the API KEY and SECRET KEY from your [Razorpay Dashboard](https://dashboard.razorpay.com/). First, log in to the dashboard, then go to <mark>Account Settings &gt; </mark> [<mark>API keys</mark>](https://dashboard.razorpay.com/app/website-app-settings/api-keys). Add the keys in `.env`

```yaml
RAZORPAY_API_KEY=rzp_test_XXXXXXXXXX
RAZORPAY_API_SECRET=XXXXXXXXXXXXXXXXX
```

## **Step 4 - Install the Razorpay Composer Package**

Install the razorpay composer package to handle the payment related activities in Laravel Application.

```bash
composer require razorpay/razorpay
```

This command will download and install the Razorpay PHP SDK into your Laravel project.

## Step 5 - Create a Table and Model to Store the Razorpay Events Response

Now we are going to create a model and table for this setup using this below command.

```bash
php artisan make:model Payment --migration
```

Now the Migration and Model Files are generated. Update the table schema based on your need.

![migration for create payment table in razorpay integration in laravel](https://cdn.hashnode.com/res/hashnode/image/upload/v1706370105411/fdb6321b-efe1-4409-95bf-9949a57f86ae.png align="center")

Here the below code for above migration and model creation.

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Payment extends Model
{
    use HasFactory;
    protected $table = 'payments';
    protected $guarded = ['id'];
}
```

```php
<?php

use Illuminate\Database\Migrations\Migration;
use Illuminate\Database\Schema\Blueprint;
use Illuminate\Support\Facades\Schema;

return new class extends Migration
{
    /**
     * Run the migrations.
     */
    public function up(): void
    {
        Schema::create('payments', function (Blueprint $table) {
            $table->id();
            $table->string('r_payment_id');
            $table->string('method');
            $table->string('currency');
            $table->string('email');
            $table->string('phone');
            $table->string('amount');
            $table->string('status');
            $table->longText('json_response');
            $table->timestamps();
        });
    }

    /**
     * Reverse the migrations.
     */
    public function down(): void
    {
        Schema::dropIfExists('payments');
    }
};
```

<mark>Execute the below command to run the migration</mark>

```bash
php artisan migrate
```

## Step 6 - Create a Controller and Views

Create a RazorpayController to handle the request and response based actions in the application and UI Design in the views.

Execute the below command to create the controller and view

```bash
 php artisan make:controller RazorpayController
 php artisan make:view razorpay/index
 php artisan make:view components/razorpay-form 
 php artisan make:view errors/402
```

![view and controller creation in razorpay integration in laravel](https://cdn.hashnode.com/res/hashnode/image/upload/v1706379088092/fedfaade-6d18-4191-8529-4073a3d6b6be.png align="center")

![error page for create error failure in razorpay integration in laravel](https://cdn.hashnode.com/res/hashnode/image/upload/v1706379119112/970b7d98-73a8-40ac-a1fd-b736035d7f75.png align="center")

<mark>The </mark> **<mark>View</mark>** <mark> Command is Only Applicable in After Laravel V10.30</mark>

In the **RazorpayController** Add the Business Logic to handle the Razorpay success and failure events scenario.

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;
use Illuminate\Contracts\View\View;
use Illuminate\Support\Facades\Log;
use Illuminate\Support\Facades\Session;
use App\Models\Payment;
use Illuminate\Http\JsonResponse;
use Illuminate\Support\Facades\DB;
use Razorpay\Api\Api;

class RazorpayController extends Controller
{
    public function index(): View
    {
        try {
            return view('razorpay.index');
        } catch (\Throwable $th) {
            Log::error('PAYMENT_INDEX_ERROR'.$th->getMessage());
        }
    }

    public function store(Request $request): JsonResponse
    {
        DB::beginTransaction();

        try {

            $paymentResponse = $request->input('response', []);
            if (count($paymentResponse) > 0 && empty($paymentResponse['razorpay_payment_id'])) {
                Session::put('error', 'No Payment ID Found');

                return redirect()->back();
            }

            $api = new Api(env('RAZORPAY_API_KEY'), env('RAZORPAY_API_SECRET'));
            $payment = $api->payment->fetch($paymentResponse['razorpay_payment_id']);
            $response = $payment->capture(['amount' => $payment['amount']]);
            Payment::create([
                'r_payment_id' => $response->id,
                'method' => $response->method,
                'currency' => $response->currency,
                'email' => $response->email,
                'phone' => $response->contact,
                'amount' => $response->amount / 100,
                'status' => 'success',
                'json_response' => json_encode((array) $response)
            ]);

            Session::put('success', 'Payment Successful');
            DB::commit();

            return response()->json(['success' => true, 'message' => 'Payment successfully recorded']);

        } catch (\Throwable $th) {
            DB::rollBack();
            Log::error('PAYMENT_STORE_ERROR'.$th->getMessage());
            Session::put('error', $th->getMessage());

            return response()->json(['success' => false, 'error' => 'Internal Server Error'], 500);
        }
    }

    public function failure(Request $request): JsonResponse {
        DB::beginTransaction();
    
        try {
            $responseData = $request->input('response', []);
            $errorData = $responseData['error'] ?? [];
    
            Payment::create([
                'r_payment_id' => $errorData['metadata']['payment_id'] ?? null,
                'method' => $errorData['source'] ?? null,
                'currency' => 'INR',
                'email' => '', //email id for the the user
                'phone' => '', // mobile number for the user,
                'amount' => 100, // amount for the payment process
                'status' => 'failed',
                'json_response' => json_encode($responseData)
            ]);
    
            DB::commit();
            return response()->json(['success' => true, 'message' => 'Payment failure recorded']);
    
        } catch (\Throwable $th) {
            DB::rollBack();
            Log::error('PAYMENT_FAILURE_ERROR: '.$th->getMessage());
            return response()->json(['success' => false, 'error' => 'Internal Server Error'], 500);
        }
    }
}
```

To handle the payment gateway via View.

```php
{{-- resources/views/razorpay/index.blade.php --}}
<html>
<head>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.5.1/jquery.min.js" 
        crossorigin="anonymous" referrerpolicy="no-referrer"></script>
</head>
<body>
     <div>@include('components.razorpay-form')</div>
</body>
</html>
```

We have created a component form to manage Razorpay payment activities, allowing for seamless integration of the payment gateway page throughout the application, accessible via a button click.

```php
{{-- resources/views/components/razorpay-form.blade.php --}}
<form action="{{ route('razorpay.payment.store') }}" method="POST">
    @csrf
    <script src="https://checkout.razorpay.com/v1/checkout.js"></script>
    <button id="payBtn">Pay 100 INR
    </button>
</form>

<script>
    var options = {
        "key": "{{ env('RAZORPAY_API_KEY') }}",
        "amount": "10000",
        "name": "Dhanar98",
        "description": "Razorpay payment",
        "image": "https://cdn.razorpay.com/logos/NSL3kbRT73axfn_medium.png",
        "prefill": {
            "name": "ABC",
            "email": "abc@gmail.com"
        },
        "theme": {
            "color": "#0F408F"
        },
        "handler" : function(res) {
            console.log(res);

            $.ajax({
                url: "/payment/create",
                type: 'POST',
                dataType: 'json',
                data: {
                    _token: "{{ csrf_token() }}", // CSRF token
                    response: {
                        razorpay_payment_id: res.razorpay_payment_id
                    }
                },
                success: function(res) {
                    console.log('Payment data sent to server', res);
                    if (res.success = true) {
                        window.location.href = '/'; //payment failure
                    }
                },
                error: function(jqXHR, textStatus, errorThrown) {
                    console.log('Error sending payment failure information:', textStatus, errorThrown);
                }
            });
        },
        "modal": {
            "ondismiss": function() {
                // This function is called when the user closes the modal
                window.location.href = '/'; // Redirect to your failure page
            }
        }
    };

    var rzp = new Razorpay(options);
    document.getElementById('payBtn').onclick = function(e) {
        rzp.open();
        e.preventDefault();
    }

    rzp.on('payment.failed', function(response) {

        event.preventDefault();
        if (response.reason = "payment_failed") {
            const {
                error,
                reason
            } = response;
            $.ajax({
                url: "/payment/failure",
                type: 'POST',
                dataType: 'json',
                data: {
                    _token: "{{ csrf_token() }}", // CSRF token
                    response: {
                        error,
                        reason
                    }
                },
                success: function(response) {
                    console.log('Payment failure data sent to server', response);
                    if (response.success = true) {
                        window.location.href = '/402'; //payment failure
                    }
                },
                error: function(jqXHR, textStatus, errorThrown) {
                    console.log('Error sending payment failure information:', textStatus, errorThrown);
                }
            });
        }
    });
</script>
```

Handling payment Failure created a error page in errors folder in views.

```php
<!DOCTYPE html>
<html>
<head>
    <title>Payment Required</title>
</head>
<body>
    <h1>402 Payment Required</h1>
</body>
</html>
```

## Step 7 - Create a Routes To Handle Requests

To create a requests in the `web.php` to handle the success and failure events.

```php
<?php

use App\Http\Controllers\RazorpayController;
use Illuminate\Support\Facades\Route;

Route::get('/', function () {
    return view('welcome');
});

Route::get('payment',[RazorpayController::class,'index']);
Route::post('payment/create',[RazorpayController::class,'store'])->name('razorpay.payment.store');
Route::post('payment/failure',[RazorpayController::class,'failure'])->name('razorpay.payment.failure');
Route::get('/402', function () {
    return view('errors.402');
});
```

## Step 8 - Run the Application

To run the application execute the command in terminal.

```bash
php artisan serve
```

<mark>I run my application in </mark> [<mark>laragon </mark>](https://laragon.org/index.html) <mark>it creates a seperate APP_URL for every project i created. if you're working very long in XAMPP try </mark> [<mark>laragon</mark>](https://laragon.org/index.html) <mark> you will never go XAMPP again. so i don't need this command also (Windows OS) only.</mark>

## Conclusion:

In this article I covered all the steps to integrate razorpay in Laravel 10 Application and handling success and error response in the payment gateway controller.

Share your colleague or friend who is struggling to integrate razorpay and support my work from coindrop.

### GITHUB Repository:

* [https://github.com/dhanar98/IntegrateRazorpayInLaravel](https://github.com/dhanar98/IntegrateRazorpayInLaravel)
    
* Article Commits step by step - [https://github.com/dhanar98/IntegrateRazorpayInLaravel/commits/master/](https://github.com/dhanar98/IntegrateRazorpayInLaravel/commits/master/)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Connect with Me:</strong></div>
</div>

<center>
[![Gmail](https://img.shields.io/badge/gmail-F44336?style=for-the-badge&amp;logo=gmail&amp;logoColor=white)](mailto:dhanasekarravi98@gmail.com)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&amp;logo=linkedin&amp;logoColor=white)](https://www.linkedin.com/in/dhanar98/)
[![Whatsapp](https://img.shields.io/badge/WhatsApp-25D366.svg?style=for-the-badge&amp;logo=WhatsApp&amp;logoColor=white)](https://wa.me/9025165942/?text=hi%20%2C%20ping%20you%20from%20via%20hashnode%20blog)
</center>