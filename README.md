# Android Boilerplate AppyHigh
## Firebase In-App Messaging
1. Make sure you have added firebase to your project.  
2. Add the following lines to your app level build.gradle file.
```
implementation 'com.google.firebase:firebase-inappmessaging-display:19.0.6'
implementation 'com.google.firebase:firebase-analytics:17.4.0'
```
3. To handle message clicks, 
	* Add the following import statements in your Kotlin code.
	```
	import com.google.firebase.inappmessaging.FirebaseInAppMessagingClickListener
	import com.google.firebase.inappmessaging.model.Action
	import com.google.firebase.inappmessaging.model.InAppMessage
	```
	* Extend *FirebaseInAppMessagingClickListener* and override *messageClicked* function as shown
	```
	override fun messageClicked(
        inAppMessage: InAppMessage,
        action: Action
    ) {
        Log.d(
            TAG,
            "messageClicked() called with: inAppMessage = [$inAppMessage], action = [$action]"
        )
        // Determine which URL the user clicked
        val url = action.actionUrl
        Log.d(TAG, "messageClicked: $url")
        // Get general information about the campaign
        val metadata = inAppMessage.campaignMetadata
        // Get data bundle for the inapp message
        val dataBundle: Map<*, *>? = inAppMessage.data
    }

    companion object {
        private const val TAG = "MyClickListener"
    }
	```
