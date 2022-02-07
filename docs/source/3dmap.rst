Point Cloud Map Edit & Download (3D)
====================================

Below is the Point Cloud Map details page.
We could use the mouse wheel to zoom in/out and right click&drag to move around the map.

.. image:: ./_static/imgs/screenshots/pcd_page.png
   :align: center

.. |download_btn| image:: ./_static/imgs/screenshots/download_btn.png

Edit
----

Coming soon...


Download Costmap
----------------

Our algorithm will generate 2D costmap automatically. The costmap is 100% compatable with robots.

Download via site
"""""""""""""""""

* Click |download_btn| on the right side of map details page
* Input the lider height to the ground and resolution of the costmap

  .. image:: ./_static/imgs/screenshots/3d_download_input.png
     :align: center

* Click :code:`OK` to download the :code:`map.zip` to your PC. The :code:`map.zip` includes:

  * :code:`map.png`, the costmap
  * :code:`map.yaml`, the related YAML file of the costmap


API Fetch Map
"""""""""""""

.. |profile_icon| image:: ./_static/imgs/screenshots/profile_icon.png
.. |access_token_btn| image:: ./_static/imgs/screenshots/access_token_btn.png

* Click :code:`Profile & Token` link under |profile_icon| and land to :code:`Profile & Token` page.
* Click |access_token_btn| button and get the token.
* Download map via our API *(bash code)*

  .. code:: bash

     curl -v -o map.zip -X GET "http://api.motivedge.io/map/MAP_ID/2d?h=0.5&r=0.05&me_token=TOKEN"

  * :code:`MAP_ID` could be found in the map details page.
    *(Next to the map name)*
  * :code:`me_token` is the generated token using above button.
    *(Required field)*
  * :code:`h` means the lidar height to the ground.
    *(Required field)*
  * :code:`r` means the 2D map resolution for each pixel. Default value is 0.05.
    *(Optional field)*

* The fetched map zip file includes :code:`map.yaml` and :code:`map.png` (costmap).
  We could unzip the file *(bash code)*:

  .. code:: bash

     unzip map.zip

* Now we could see the map in our system and we could update our robot :code:`map_server` to use this latest map.

.. attention:: **SDK will release soon**

   Our SDK is under developing and will be released soon. We don't need above
   complicated fetch map steps after releasing.

   **Only one line of code will finish above all.**
