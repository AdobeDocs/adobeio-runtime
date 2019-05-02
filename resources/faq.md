# Adobe I/O Runtime: Frequently Asked Questions

On this page: 
- [Getting Access ](#gettingaccess)
- [Supported Programming Languages](#supportedprogramminglanguages)
- [Price](#price)
- [Usage Quota](#usagequota)
- [Where we execute your actions](#multipleregionsupport)
- [System Limits](#systemlimits)

## Getting Access 
**How can I get access to I/O Runtime?**  
I/O Runtime is in private beta. You can sign up [here](https://adobeio.typeform.com/to/RWhT8Y) to get notified when it is general available.

## Supported Programming Languages 
**Which languages are supported in I/O Runtime?**  
For now, Adobe I/O Runtime only supports Node.js. We will add support for other languages as the platform matures.

## Price 
**What does it cost to use Adobe I/O Runtime?**  
Presently (private beta), Adobe I/O Runtime is free to use for Adobe enterprise customers and partners.

## Usage Quotas 
**What usage quotas are in place for Adobe I/O Runtime?**  
There are presently no usage quotas on Adobe I/O Runtime.

## Multiple Region Support
**Where we execute your actions**
I/O Runtime runs in AWS US-East and Euriope-West. We deploy your code in all regions and execute it in the closest region to the caller (latency-based routing).

## System Limits
**Which limits are imposed onto actions?**  
All available limits (and the default values) are listed here: [System Settings](../guides/system_settings.md). Notable limits are the timeout for functions and the maximum payload that can get posted to a function.