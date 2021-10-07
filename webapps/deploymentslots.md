## Deployment slots 

Deployment slots are live apps with their own hostnames. App content and configurations elements can be swapped between two deployment slots, including the production slot.
Using separate staging and production slots has several advantages.

- You can validate app changes in a staging deployment slot before swapping it with the production slot.
- Deploying an app to a slot first and swapping it into production ensures that all instances of the slot are warmed up before being swapped into production. This eliminates downtime when you deploy your app. The traffic redirection is seamless, and no requests are dropped because of swap operations. This entire workflow can be automated by configuring Auto Swap when pre-swap validation is not needed.
- After a swap, the slot with previously staged app now has the previous production app. If the changes swapped into the production slot are not as you expected, you can perform the same swap immediately to get your “last known good site” back.- 

For the new web app, you created only one slot: the production slot. You deployed source code to this slot.

Next, you'll create a deployment slot where you can stage new versions of the web app.

## (option a) Create a new Preproduction Slot with CLI 
```
az webapp deployment slot  create  -s preprod -n nynynynsg1 -g ivanresourcegroup
```
## (option b)Create a new Preproduction Slot in the Portal 
Create a new staging slot

- On the Azure portal menu, or from the Home page, select All resources, filter by Type == App Service, and then select Apply.
- Select your web app. The App Service pane appears for your web app.
- In the left menu pane, under Deployment, select Deployment slots. The Deployment slots pane appears for your App Service
- ![registry](./img/1slot.png)
- From the top menu bar, select Add Slot. The Add a slot pane appears.
- In the Name field, enter Staging, accept the default for Clone settings from, and then select Add.
- After the deployment slot is successfully created, select Close.

## 
```
az webapp deployment slot  create  -s preprod -n nynynynsg1 -g ivanresourcegroup
```







