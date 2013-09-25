celeryd-init-script
===================

Celery init script with replace option.

Usage:

/etc/init.d/celeryd {start|stop|restart|replace} [worker-name]"
/etc/init.d/celeryd {restart-workers-graceful|kill|create-paths}"

Configuration file: /etc/default/celeryd

Original code: https://github.com/celery/celery/blob/master/extra/generic-init.d/celeryd
See http://docs.celeryproject.org/en/latest/tutorials/daemonizing.html#generic-init-scripts

To implement separate init scripts, do NOT copy this script.  Instead, symlink it.  I.e., if my new application, "little-worker" needs an init, I should just use:

# ln -s /etc/init.d/celeryd /etc/init.d/little-worker

You can then configure this by manipulating /etc/default/little-worker.

If you want to have separate LSB headers in each script you can source this script instead of symlinking:
   # ...
   ### END INIT INFO
   source /etc/init.d/celeryd

Setting `SCRIPT_NAME` here allows you to symlink/source this init script,
making it easy to run multiple processes on the system.
