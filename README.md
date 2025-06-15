Simple explanation here:




Drawable drawable = ResourcesCompat.getDrawable(getResources(), R.drawable.icon, null);
        BitmapDrawable bitmapDrawable = (BitmapDrawable) drawable;
        Bitmap largeIcon = null;
        if (bitmapDrawable != null) {
            largeIcon = bitmapDrawable.getBitmap();
        }

        Notification notification;

        NotificationManager notificationManager = (NotificationManager) getSystemService(NOTIFICATION_SERVICE);
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            notification = new Notification.Builder(this)
                    .setLargeIcon(largeIcon)
                    .setSmallIcon(R.drawable.icon)
                    .setContentText("New Message")
                    .setSubText("Message from Monir")
                    .setChannelId(CHANNEL_ID)
                    .build();
            notificationManager.createNotificationChannel(new NotificationChannel(CHANNEL_ID, "My Channel1", NotificationManager.IMPORTANCE_HIGH));
        }
        else {
            notification = new Notification.Builder(this)
                    .setLargeIcon(largeIcon)
                    .setSmallIcon(R.drawable.icon)
                    .setContentText("New Message")
                    .setSubText("Message from Monir")Add commentMore actions
                    .build();
        }

        notificationManager.notify(NOTIFICATION_ID, notification);
