### donation_form
A Drupal 8 module for accepting donations; leverages Stripe for payment processing.
___

# User instructions
How to install and use . . .

___
# Development Documentation
## Requirements

    
#### Installation requirements: 

The donation form should ideally work with two installation steps: 1) installing Drupal (including composer install) 2) enabling one custom module containing your configuration and custom code.
* Stripe PHP library is a requirement, this should be required in a composer.json within the module.
* Include config within the module so everything's ready to go when module is enabled
* Make sure Drupal module dependencies are also documented.


#### Use requirements:

Need to collect who is making the donation, how much it’s for and of course collect the credit card payment.
* Drupal will collect this user identity and donation ammount in addition to integrating with Stripe to process payment.

**It would be nice to also**: 
* Allow the user to select from a list of donation amounts or enter a custom value.
* Track the status of the transaction from Stripe in Drupal with a record of the donation.  A view might also be nice
* Realtime validation of inputs.
* 

### Module selection

There are a number of Stripe module for Drupal, I want to pick one that is stable, suits this use case well, and can be implemented fairly quickly.


___