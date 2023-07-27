# freebsd-update-notify

Freebsd-update-notify is a script invoked by cron to check for available
updates and issue popup notification on the desktop.  The user can elect
to install and reboot or ignore them until the next cron check.

Two cron entries are installed:

1.  Frequently run freebsd-update cron to download available base system
    updates.  Freebsd-update cron is only run if another process is not
    already running and no updates have been downloaded and are awaiting
    installation.

2.  A few times a day by default, check for downloaded base updates
    and the time since auto-update-system was last completed successfully.
    If either base updates are available or a week has passed since the
    last update, a popup message is displayed on the console screen (:0).
    If the user clicks "Yes", "auto-update-system --defaults" is run
    to update packages, the ports tree, and the base system.
