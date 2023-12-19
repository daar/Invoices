## Installation

```
composer require daar/invoices
```


Example Usage:

```php
$invoice = \Daar\Invoices\Classes\Invoice::make()
                ->addItem('Test Item', 10.25, 2, 1412)
                ->addItem('Test Item 2', 5, 2, 923)
                ->addItem('Test Item 3', 15.55, 5, 42)
                ->addItem('Test Item 4', 1.25, 1, 923)
                ->addItem('Test Item 5', 3.12, 1, 3142)
                ->addItem('Test Item 6', 6.41, 3, 452)
                ->addItem('Test Item 7', 2.86, 1, 1526)
                ->addItem('Test Item 8', 5, 2, 923, 'https://dummyimage.com/64x64/000/fff')
                ->number(4021)
                ->with_pagination(true)
                ->duplicate_header(true)
                ->due_date(Carbon::now()->addMonths(1))
                ->notes('Lrem ipsum dolor sit amet, consectetur adipiscing elit.')
                ->customer([
                    'name'      => 'Èrik Campobadal Forés',
                    'id'        => '12345678A',
                    'phone'     => '+34 123 456 789',
                    'location'  => 'C / Unknown Street 1st',
                    'zip'       => '08241',
                    'city'      => 'Manresa',
                    'country'   => 'Spain',
                ])
                ->download('demo');
```





![Sample Invoice](https://camo.githubusercontent.com/a179f76efacbe1db1d6e06a36878558f90070697/68747470733a2f2f692e6779617a6f2e636f6d2f37363866356235393739313136326534333266396364666131356630313762632e706e67)








Daar\Invoices\InvoicesServiceProvider
===============

This is the InvoicesServiceProvider class.




* Class name: InvoicesServiceProvider
* Namespace: Daar\Invoices
* Parent class: Illuminate\Support\ServiceProvider







Methods
-------


### boot

    void Daar\Invoices\InvoicesServiceProvider::boot()

Bootstrap any application services.



* Visibility: **public**




### register

    void Daar\Invoices\InvoicesServiceProvider::register()

Register any application services.


* Visibility: **public**




























Daar\Invoices\Classes\PDF
===============

This is the PDF class.




* Class name: PDF
* Namespace: Daar\Invoices\Classes







Methods
-------


### generate

    \Dompdf\Dompdf\Dompdf Daar\Invoices\Classes\PDF::generate(\Daar\Invoices\Classes\Daar\Invoices\Classes\Invoice $invoice, string $template)

Generate the PDF.



* Visibility: **public**
* This method is **static**.


#### Arguments
* $invoice **Daar\Invoices\Classes\Daar\Invoices\Classes\Invoice**
* $template **string**






































Daar\Invoices\Classes\Invoice
===============

This is the Invoice class.




* Class name: Invoice
* Namespace: Daar\Invoices\Classes





Properties
----------


### $name

    public string $name

Invoice name.



* Visibility: **public**


### $template

    public string $template

Invoice template.



* Visibility: **public**


### $items

    public \Daar\Invoices\Classes\Illuminate\Support\Collection $items

Invoice item collection.



* Visibility: **public**


### $currency

    public string $currency

Invoice currency.



* Visibility: **public**


### $tax

    public integer $tax

Invoice tax.



* Visibility: **public**


### $tax_type

    public string $tax_type

Invoice tax type.



* Visibility: **public**


### $number

    public integer $number = null

Invoice number.



* Visibility: **public**


### $decimals

    public integer $decimals

Invoice decimal precision.



* Visibility: **public**


### $logo

    public string $logo

Invoice logo.



* Visibility: **public**


### $logo_height

    public integer $logo_height

Invoice Logo Height.



* Visibility: **public**


### $date

    public \Carbon\Carbon\Carbon $date

Invoice Date.



* Visibility: **public**


### $notes

    public string $notes

Invoice Notes.



* Visibility: **public**


### $business_details

    public array $business_details

Invoice Business Details.



* Visibility: **public**


### $customer_details

    public array $customer_details

Invoice Customer Details.



* Visibility: **public**


### $footnote

    public array $footnote

Invoice Footnote.



* Visibility: **public**


### $pdf

    private \Daar\Invoices\Classes\Dompdf\Dompdf $pdf

Stores the PDF object.



* Visibility: **private**


Methods
-------


### __construct

    mixed Daar\Invoices\Classes\Invoice::__construct(string $name)

Create a new invoice instance.



* Visibility: **public**


#### Arguments
* $name **string**



### make

    \Daar\Invoices\Classes\Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::make(string $name)

Return a new instance of Invoice.



* Visibility: **public**
* This method is **static**.


#### Arguments
* $name **string**


### template

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::template(string $template)

Select template for invoice.

* Visibility: **public**
* Default: **default**


#### Arguments
* $name **template**

### addItem

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::addItem(string $name, integer $price, integer $ammount, string $id)

Adds an item to the invoice.



* Visibility: **public**


#### Arguments
* $name **string**
* $price **integer**
* $ammount **integer**
* $id **string**



### popItem

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::popItem()

Pop the last invoice item.



* Visibility: **public**




### formatCurrency

    \Daar\Invoices\Classes\stdClass Daar\Invoices\Classes\Invoice::formatCurrency()

Return the currency object.



* Visibility: **public**




### subTotalPrice

    integer Daar\Invoices\Classes\Invoice::subTotalPrice()

Return the subtotal invoice price.



* Visibility: **public**




### totalPrice

    integer Daar\Invoices\Classes\Invoice::totalPrice()

Return the total invoce price after aplying the tax.



* Visibility: **public**




### taxPrice

    float Daar\Invoices\Classes\Invoice::taxPrice()

taxPrice.



* Visibility: **public**




### generate

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::generate()

Generate the PDF.



* Visibility: **private**




### download

    \Daar\Invoices\Classes\response Daar\Invoices\Classes\Invoice::download(string $name)

Downloads the generated PDF.



* Visibility: **public**


#### Arguments
* $name **string**



### shouldDisplayImageColumn

    \Daar\Invoices\Classes\response Daar\Invoices\Classes\Invoice::shouldDisplayImageColumn()

Return true/false if one item contains image.
Determine if we should display or not the image column on the invoice.



* Visibility: **public**



### show

    \Daar\Invoices\Classes\response Daar\Invoices\Classes\Invoice::show(string $name)

Show the PDF in the browser.



* Visibility: **public**


#### Arguments
* $name **string**



### name

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::name(string $name)

Set the invoice name.



* Visibility: **public**


#### Arguments
* $name **string**



### number

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::number(integer $number)

Set the invoice number.



* Visibility: **public**


#### Arguments
* $number **integer**



### decimals

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::decimals(integer $decimals)

Set the invoice decimal precision.



* Visibility: **public**


#### Arguments
* $decimals **integer**



### tax

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::tax(float $tax)

Set the invoice tax.



* Visibility: **public**


#### Arguments
* $tax **float**



### taxType

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::taxType(string $tax_type)

Set the invoice tax type.



* Visibility: **public**


#### Arguments
* $tax_type **string**



### logo

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::logo(string $logo_url)

Set the invoice logo URL.



* Visibility: **public**


#### Arguments
* $logo_url **string**



### date

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::date(\Carbon\Carbon $date)

Set the invoice date.



* Visibility: **public**


#### Arguments
* $date **Carbon\Carbon**



### notes

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::notes(string $notes)

Set the invoice notes.



* Visibility: **public**


#### Arguments
* $notes **string**



### business

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::business(array $details)

Set the invoice business details.



* Visibility: **public**


#### Arguments
* $details **array**



### customer

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::customer(array $details)

Set the invoice customer details.



* Visibility: **public**


#### Arguments
* $details **array**



### footnote

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::footnote(string $footnote)

Set the invoice footnote.



* Visibility: **public**


#### Arguments
* $footnote **string**



### due_date

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::due_date(Carbon $due_date)

Set the invoice due date.



* Visibility: **public**


#### Arguments
* $due_date **Carbon**



### tax_rates

Array of tax rates for invoices.



* Visibility: **public**


### with_pagination

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::with_pagination(boolean $with_pagination)

If true and page count are higher than 1, pagination will show at the bottom.



* Visibility: **public**



#### Arguments
* $duplicate_header **boolean**


### with_pagination

    \Daar\Invoices\Classes\Invoice Daar\Invoices\Classes\Invoice::duplicate_header(boolean $duplicate_header)

If true header will be duplicated on each page.



* Visibility: **public**


#### Arguments
* $duplicate_header **boolean**