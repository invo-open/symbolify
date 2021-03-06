Symbolify
=========

Symbolify enables the use of symbols with ActiveRecord. 


Why "Symbolify"?
=================

"Magic strings" have always been a problem irrespective of the programming language. Enums is one known way of avoiding these magic strings.
However we found that Ruby encourages the use of symbols instead. We found this as a good way to replace magic strings, but with a few pitfalls.

+ There is no way to store these symbols as symbols in active record. It needed to be stored as string

+ While retrieving and saving to the database the symbols needed to be converted which necessitated a lot of unnecessary work

In order to avoid such confusions, we came up with the idea of Symbolify. Symbolify takes care of all the conversions needed while saving to and retrieving from the database.

With Symbolify you can

+ Convert a string to an equivalent symbol (eg. ruby --> :ruby) and vice-versa (eg. :ruby --> ":ruby")

+ With the help of these conversions, you can send and receive these symbols to and from the client side quite easily.

+ Saving to and retrieving from the database using ActiveRecord has been simplified to a great extent.

Usage
=====

+	Copy the entire plugin into __vendor/plugins/__ folder or execute

		rails plugin install git://github.com/invoscape/symbolify.git

+	You get two methods
	to_eqv_s - To convert a symbol to string
	to_eqv_sym - To convert a string to symbol
		
+	In the model (say Payment) where you want to expose an attribute (say payment_status) as symbol, name your column as payment_status_symbol

+	Include this line in the model along with other attr_accessors
		
		class Payment < ActiveRecord::Base
			symbol_attribute :payment_status
		end
		
+	To get the value as symbol refer the attribute as payment.payment_status.
	Similarly you get a setter eg. payment.payment_status = :paid

+	While using finder methods mention the original column name i.e. payment_status_symbol
	eg. Payment.find_by_payment_status_symbol(:paid.to_eqv_s)

__Home page__ - [invoscape.com/open_source#symbolify](http://www.invoscape.com/open_source#symbolify)

__Want to contribute ?__ - Drop in a mail to opensource(at)invoscape(dot)com

Please do report any issues you face - [issues](https://github.com/invoscape/symbolify/issues)

Copyright &copy; [Invoscape Technologies Pvt. Ltd.](http://www.invoscape.com), released under the MIT license
