<!-- default badges list -->
![](https://img.shields.io/endpoint?url=https://codecentral.devexpress.com/api/v1/VersionRange/128535207/15.1.5%2B)
[![](https://img.shields.io/badge/Open_in_DevExpress_Support_Center-FF7200?style=flat-square&logo=DevExpress&logoColor=white)](https://supportcenter.devexpress.com/ticket/details/E3578)
[![](https://img.shields.io/badge/📖_How_to_use_DevExpress_Examples-e9f6fc?style=flat-square)](https://docs.devexpress.com/GeneralInformation/403183)
[![](https://img.shields.io/badge/💬_Leave_Feedback-feecdd?style=flat-square)](#does-this-example-address-your-development-requirementsobjectives)
<!-- default badges end -->
# Grid View for ASP.NET Web Forms - How to refresh a master grid on a detail grid callback

This example demonstrates how to use the callback functionality to update the master grid when detail grid data changes.

## Overview

Handle the detail grid's client-side [BeginCallback](https://docs.devexpress.com/AspNet/js-ASPxClientGridView.BeginCallback) and [EndCallback](https://docs.devexpress.com/AspNet/js-ASPxClientGridView.EndCallback) events to refresh the master grid control when a callback is finished. Use the `command` argument property to determine the action that initiates that callback.

```aspx
<dx:ASPxGridView ID="ASPxGridView1" runat="server" KeyFieldName="Id" ... >
    <SettingsDetail ShowDetailRow="true" />
    <!-- ... -->
    <Templates>
        <DetailRow>
            <dx:ASPxGridView ID="gridProducts" runat="server" KeyFieldName="Id" ... >
                    <ClientSideEvents EndCallback="OnEndCallback" BeginCallback="OnBeginCallback" />
                <!-- ... -->
            </dx:ASPxGridView>
        </DetailRow>
    </Templates>
</dx:ASPxGridView>
```

```js
var command = "";
function OnBeginCallback(s, e) {
    command = e.command;
}
function OnEndCallback(s, e) {
    if (command == "ADDNEWROW") {
        s.Refresh();
    }
}
```

## Files to Review

* [OrderItems.cs](./CS/WebSite/App_Code/OrderItems.cs) (VB: [OrderItems.vb](./VB/WebSite/App_Code/OrderItems.vb))
* [Default.aspx](./CS/WebSite/Default.aspx) (VB: [Default.aspx](./VB/WebSite/Default.aspx))

## Documentation

* [Update a Control in a Callback of Another Control](https://docs.devexpress.com/AspNet/402219/common-concepts/callbacks/update-control-in-callback-of-another-control)
<!-- feedback -->
## Does this example address your development requirements/objectives?

[<img src="https://www.devexpress.com/support/examples/i/yes-button.svg"/>](https://www.devexpress.com/support/examples/survey.xml?utm_source=github&utm_campaign=asp-net-web-forms-grid-refresh-master-grid-on-detail-grid-callback&~~~was_helpful=yes) [<img src="https://www.devexpress.com/support/examples/i/no-button.svg"/>](https://www.devexpress.com/support/examples/survey.xml?utm_source=github&utm_campaign=asp-net-web-forms-grid-refresh-master-grid-on-detail-grid-callback&~~~was_helpful=no)

(you will be redirected to DevExpress.com to submit your response)
<!-- feedback end -->
