## Integration Overview and Rationale

Integrating Spayment's APIs into your application is designed to be a seamless process, allowing you to quickly enable payment functionality without extensive development effort. Below, we provide an overview of the integration process and the rationale behind the design of our APIs.

### Integration Process

1. **API Endpoints**: We offer two main API endpoints - `demo_checkout.php` and `live_checkout.php`. These endpoints cater to different environments: `demo_checkout.php` is meant for testing and development purposes, while `live_checkout.php` is for production use.

2. **Request Parameters**: To initiate a payment transaction, you need to provide specific request parameters such as `email`, `public_key`, `private_key`, `redirect_url`, and `amount`. These parameters are essential for authenticating the transaction and specifying payment details.

3. **Response Handling**: Responses from the API are sent through a cookie named `verification_transaction_spay`, enabling dynamic interaction with the payment form. Successful transactions result in a `00` response code, triggering the setting of the `verification_transaction_spay` cookie and redirection to the specified `redirect_url`. Error responses provide meaningful feedback to users regarding validation errors, network issues, or specific error codes from the Spayment gateway.

4. **Example Usage**: We provide clear examples of how to use the API endpoints in HTML forms, demonstrating the required parameters and submission process. This facilitates quick integration into your application, requiring minimal coding effort.

### Time to Integration

The integration process with Spayment's APIs is designed to be efficient, allowing developers to seamlessly incorporate payment functionality into their applications in less than 10 minutes. By providing straightforward API endpoints, clear documentation, and example usage, we aim to streamline the integration process and minimize development overhead.

### Rationale

- **Developer Experience**: We prioritize developer experience by offering intuitive APIs and comprehensive documentation. By simplifying the integration process, developers can focus on building innovative features without being burdened by complex payment setups.

- **Flexibility**: The separation of `demo_checkout.php` and `live_checkout.php` endpoints provides flexibility for developers to test payment functionality in a controlled environment before deploying to production. This approach ensures a smooth transition from development to live deployment.

- **Security**: We emphasize security best practices by securely managing API keys and avoiding their exposure in client-side code or public repositories. This protects sensitive information and mitigates potential security risks associated with payment processing.

In summary, Spayment's APIs are designed to offer a seamless integration experience, prioritizing developer convenience, flexibility, and security. Our goal is to empower developers to effortlessly incorporate payment functionality into their applications, enabling smooth transactions for users.


## Demo checkout

### Description
The `demo_checkout.php` file serves as an endpoint for initiating a payment transaction through the Spayment gateway. It handles the validation of API keys, processing of payment requests, and interaction with the payment form.

### Endpoint
```
https://api.spayement.com.ng/v1/demo_checkout.php
```

### Request Parameters
- **email**: Email address of the user initiating the payment. *(Required)*
- **public_key**: Public API key provided by Spayment for authentication. *(Required)*
- **private_key**: Private API key provided by Spayment for authentication. *(Required)*
- **redirect_url**: URL to redirect the user after a successful payment transaction. *(Required)*
- **amount**: Amount to be charged for the transaction. *(Required)*

### Response
Responses from `demo_checkout.php` are sent through a cookie named `verification_transaction_spay`. The responses are also handled dynamically through JavaScript interactions with the payment form.

#### Successful Response
If the payment transaction is successful, the response code will be `00`. In this case, the following actions are performed:
1. A cookie named `verification_transaction_spay` is set to `success`.
2. The user is redirected to the specified `redirect_url`.

#### Error Response
If there is an error during the payment transaction, appropriate error messages are displayed to the user via the payment form. Error responses include validation errors, network errors, or specific error codes returned by the Spayment gateway.

### Example Usage
```html
<!-- Example Usage of demo_checkout.php -->
<form action="https://api.spayement.com.ng/v1/demo_checkout.php" method="GET">
    <input type="hidden" name="email" value="user@example.com">
    <input type="hidden" name="public_key" value="your_public_key">
    <input type="hidden" name="private_key" value="your_private_key">
    <input type="hidden" name="redirect_url" value="https://example.com/success">
    <input type="hidden" name="amount" value="1000">
    <button type="submit">Proceed to Payment</button>
</form>
```

### Notes
- Ensure that the provided API keys (public_key and private_key) are valid and associated with your Spayment account.
- The `redirect_url` should be a valid URL where users will be redirected after completing the payment transaction.
- For security reasons, never expose private API keys in client-side code or public repositories.

## Live checkout

### Description
The `checkout.php` file serves as an endpoint for initiating a payment transaction through the Spayment gateway in a live environment. It functions similarly to `demo_checkout.php` but is intended for production use.

### Endpoint
```
https://api.spayement.com.ng/checkout.php
```

### Usage
The usage of `checkout.php` is identical to `demo_checkout.php`. Please refer to the documentation for `demo_checkout.php` for details on request parameters, responses, and example usage.

### Notes
- Use `checkout.php` in your production environment to process real payment transactions.
- Follow the same security and best practices outlined in the documentation for `demo_checkout.php`.
- Ensure that your production API keys (public_key and private_key) are securely managed and never exposed in client-side code or public repositories.
