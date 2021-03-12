# FraudLabs Pro Python SDK

Модуль позволяет подключатьс к сервису [fraudlabspro.com](https://fraudlabspro.com), который позволяет защитить бизнес в online. 

Ниже представлены модули, которые позволяют
- составить скоринг
- валидация банковских карт
- верификация и валидация через СМС

## Примеры использования
```python
 # import SDK to use the function
from fraudlabspro.order import Order

api_key = 'YOUR_API_KEY'  # API Ключ

 # Данные заказа
dict1 = {
	'key': api_key,
	'ip': '11.22.33.44',
	'order': {
		'order_id': '123', 
		'currency': 'USD',
		'amount': '100',
		'quantity': 1, 
		'paymentMethod': 'creditcard'
	},
	'card': {
		'number': '4556553172971283'
	},
	'billing': {
		'firstName': 'Ivan',
		'lastName': 'Ivanov',
		'email': 'example@yandex.ru',
		'phone': '561-628-8674',
		'address': 'Frunze 1',
		'city': 'Moscow',
		'state': 'Moscow',
		'country': 'RU',
	},
}

result = Order.validate(dict1)  # Проверка
```

### Свойства объекта
| Property Name        | Property Type | Description                                                  |
| -------------------- | ------------- | ------------------------------------------------------------ |
| ip                   | string        | IP address of online transaction. It supports both IPv4 and IPv6 address format. |
| billing->firstName   | string        | User's first name.                                           |
| billing->lastName    | string        | User's last name.                                            |
| billing->username    | string        | User's username.                                             |
| billing->password    | string        | User's password.                                             |
| billing->email       | string        | User's email address.                                        |
| billing->phone       | string        | User's phone number.                                         |
| billing->address     | string        | Street address of billing address.                           |
| billing->city        | string        | City of billing address.                                     |
| billing->state       | string        | State of billing address. It supports state codes, e.g. NY (New York), for state or province of United States or Canada. Please refer to [State & Province Codes](https://www.fraudlabspro.com/developer/reference/state-and-province-codes) for complete list. |
| billing->postcode    | string        | Postal or ZIP code of billing address.                       |
| billing->country     | string        | Country of billing address. It requires the input of ISO-3166 alpha-2 country code, e.g. US for United States. Please refer to [Country Codes](https://www.fraudlabspro.com/developer/reference/country-codes) for complete list. |
| order->orderId       | string        | Merchant identifier to uniquely identify a transaction. It supports maximum of 15 characters user order id input. |
| order->note          | string        | Merchant description of an order transaction. It supports maximum of 200 characters. |
| order->amount        | float         | Amount of the transaction.                                   |
| order->quantity      | integer       | Total quantity of the transaction.                           |
| order->currency      | string        | Currency code used in the transaction. It requires the input of ISO-4217 (3 characters) currency code, e.g. USD for US Dollar. Please refer to [Currency Codes](https://www.fraudlabspro.com/developer/reference/currency-codes) for complete list. |
| order->department    | string        | Merchant identifier to uniquely identify a product or service department. |
| order->paymentMethod | string        | Payment mode of transaction. Valid values: creditcard, affirm, paypal, googlecheckout, bitcoin, cod, moneyorder, wired, bankdeposit, elviauthorized, paymitco, cybersource, sezzle, viabill, amazonpay, pmnts_gateway, giftcard, others.   |
| card->number         | string        | Billing credit card number or BIN number.                    |
| card->avs            | string        | The single character AVS result returned by the credit card processor. Please refer to [AVS & CVV2 Response Codes](https://www.fraudlabspro.com/developer/reference/avs-and-cvv2-response-codes) for details. |
| card->cvv            | string        | The single character CVV2 result returned by the credit card processor. Please refer to [AVS & CVV2 Response Codes](https://www.fraudlabspro.com/developer/reference/avs-and-cvv2-response-codes) for details. |
| shipping->address    | string        | Street address of shipping address.                          |
| shipping->city       | string        | City of shipping address.                                    |
| shipping->state      | string        | State of shipping address. It supports state codes, e.g. NY - New York, for state or province of United States or Canada. Please refer to [State & Province Codes](https://www.fraudlabspro.com/developer/reference/state-and-province-codes) for complete list. |
| shipping->postcode   | string        | Postal or ZIP code of shipping address.                      |
| shipping->country    | string        | Country of shipping address. It requires the input of ISO-3166 alpha-2 country code, e.g. US for United States. Please refer to [Country Codes](https://www.fraudlabspro.com/developer/reference/country-codes) for complete list. |
