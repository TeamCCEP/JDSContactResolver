# CJDS Contact Resolver Flow

# License

All contents are licensed under the MIT license. Please see [license](LICENSE) for details.

# Disclaimer

Everything included is for demo and Proof of Concept purposes only. Use of the site is solely at your own risk. This site may contain links to third party content, which we do not warrant, endorse, or assume liability for. These demos are for Cisco Webex usecases, but are not Official Cisco Webex Branded demos.

# Questions

Please contact the CCEP team at [ccep@cisco.com](mailto:ccep@cisco.com?subject=payment-collections-demo) for questions.

### Solution Goals

See the [Vidcast Overview](https://app.vidcast.io/share/cab5b686-9745-4394-98d4-b8b58c45f1a3) for a verbal explanation!

A Webex Contact Centre flow that will take the number the user is calling in from, Resolve the rest of that users contact details against the JDS customer database, and make details such as alternative phone numbers, email addresses and customer reference numbers available for use within the flow via variables.

The flow provided is a subflow, which makes calling it from another flow simple and quick without too much configuration.

# Change Log

| Change Title  |   Date   | Details                     |
| :------------ | :------: | :-------------------------- |
| Repo Creation | 11/28/24 | Repo creation as a subflow. |

### Solution Pre-Requisites

-CJDS Tenant must be set up, functional, and have customer ID's created within it. See the [JDS V10 readme](https://github.com/CiscoDevNet/cjaas-widgets/blob/main/CustomerJourney/README_VERSION_10.0.0.md)

-Enable the [Webex Contact Centre HTTP Connector Integration](https://help.webex.com/en-us/article/n54f5wd/Create-Webex-Contact-Center-HTTP-connector)

-One Functional Inbound Voice Channel / Queue

### Installing JDS Contact Resolver Flow For Testing

1. Log into Webex Contact Centre and import the flow "JDS_ContactResolver_V3.json" as a sub flow
2. Import the flow "JDS_READER.json" as a regular flow
3. Open the "JDS_READER.json" Flow, and edit the variables JDS_Workspace_ID to include your JDS Project ID. If you wish to use debugging, Edit the variable WebHookSite to include the ID from your https://webhook.site/ Instance
4. Associate the JDS_Reader flow with an inbound telephone number
5. Call in from a number known to the JDS Solution. Monitor your Webhook.site instance for output, and listen to the played prompts to check the relevant data on that user is returned into the flow variables

### Installing the JDS Contact Resolver Flow In An Existing Flow

1.Ensure the following variables are created within your flow:

| Variable Name    | Var Type | Default Value                                                          |
| :--------------- | :------: | :--------------------------------------------------------------------- |
| firstName        |  string  |                                                                        |
| lastName         |  string  |                                                                        |
| email            |  string  |                                                                        |
| customerId       |  string  |                                                                        |
| phone0           |  string  |                                                                        |
| phone1           |  string  |                                                                        |
| personId         |  string  |                                                                        |
| firstName        |  string  |                                                                        |
| JDS_Workspace_ID |  string  | JDS Project ID from Control Hub                                        |
| WebHookSite      |  string  | Your webhook.site identifier, e.g 775c4cbc-0249-4e3a-a903-b60e656b1d39 |

2. Ensure the "JDS_ContactResolver_V3.json" flow is uploaded to your WxCC Tenant as a sub-flow. Add it into the flow that you want to use the JDS data in.
3. Ensure the above variables are mapped properly between your flow, and the JDS Contact Resolver Flow
4. Start using JDS Provided information in your flow!
