# VS Code App (Code Server)

We have added a Visual Studio Code app to the Open OnDemand interface, to provide a full-featured IDE with access to the cluster through your browser. You can set this app to run for a pre-determined amount of time, and can allocate up to 4 CPUs from the cluster to your interactive session (although we do ask that you do your best not to allocate more resources than you need).

To start, go to the "Interactive Apps" menu and select "Code Server"

![Screenshot of Open OnDemand interface](images/vscode_1.png)

You'll then be presented with some options for how many CPUs you need, and how long you expect to work for. Pick your options, then click "Launch"

![Screenshot of Open OnDemand interface](images/vscode_2.png)

You should see a screen like the screenshot below, where your Code Server session will appear queued. Depending on the resources available in the platform, your session may take several minutes to start as new compute instances are prepared for use.

![Screenshot of Open OnDemand interface](images/vscode_3.png)

Once your compute resources have been allocated and your environment is ready, you'll see that your session is "Running", and you'll have a button to launch. Click "Connect to VS Code" to access the VS Code interface.

![Screenshot of Open OnDemand interface](images/vscode_4.png)

Once you click the button to connect, you should be directed to a VS Code interface like this one. You shouldn't be prompted for a password, and if you are, that indicates an issue with how the VS Code app is working, so please reach out to support via [atg@fas.harvard.edu](mailto:atg@fas.harvard.edu)

![Screenshot of Open OnDemand interface](images/vscode_5.png)
