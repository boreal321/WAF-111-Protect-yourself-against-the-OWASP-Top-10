Lab – Install the WAF Tester Tool
---------------------------------

F5 WAF Tester
-------------

Clone the repo

::

   git clone https://github.com/f5devcentral/f5-waf-tester

Read the README to install the tool:
https://github.com/f5devcentral/f5-waf-tester

Initialize the tool

::

   f5-waf-tester --init
   [BIG-IP] Host []: 10.1.1.4
   [BIG-IP] Username []: admin
   [BIG-IP] Password []:
   ASM Policy Name []: ipi_demo
   Virtual Server URL []: http://10.1.10.101
   Blocking Regular Expression Pattern [<br>Your support ID is: (?P<id>\d+)<br>]:
   Number OF Threads [25]:
   [Filters] Test IDs to include (Separated by ',') []:
   [Filters] Test Systems to include (Separated by ',') []:
   [Filters] Test Attack Types to include (Separated by ',') []:
   [Filters] Test IDs to exclude (Separated by ',') []:
   [Filters] Test Systems to exclude (Separated by ',') []:
   [Filters] Test Attack Types to exclude (Separated by ',') []:

Edit the config if required. Much easier than re-running the init if you
made a mistake.

::

   vi ~/.local/lib/python2.7/site-packages/f5_waf_tester/config/config.json

After initialization it looks like this

::

   {
     "asm_policy_name": "ipi_demo",
     "big-ip": {
       "username": "admin",
       "host": "10.1.1.4",
       "password": "*****"
     },
     "blocking_regex": "<br>Your support ID is: (?P<id>\\d+)<br>",
     "threads": 25,
     "filters": {
       "exclude": {
         "attack_type": [],
         "id": [],
         "system": []
       },
       "include": {
         "attack_type": [],
         "id": [],
         "system": []
       }
     },
     "virtual_server_url": "http://10.1.10.101"
   }

run the tool

::

   f5-waf-tester -r f5_waf_tester_report_`date '+%s'`.json

Many of the tests failed because the signatures were out of date so
ensure the latest signatures have been installed.
https://support.f5.com/csp/article/K8217

Quickly check how many tests passed and failed

::

   grep true report.json |wc -l
   grep false report.json |wc -l

Task – Title here
~~~~~~~~~~~~~~~~~


   .. DANGER:: Knives are sharp and can cut you.  Please be careful.

      |knivessharp|

#. Carefully remove the |bip| from it's packaging
#. Set it down on a stable surface

.. |knivessharp| image:: http://theinkkitchen.com/wp-content/uploads/2014/08/Screenshot-2014-07-30-12.22.44.png
