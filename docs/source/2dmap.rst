Costmap Edit & Download (2D)
============================

Below is the costmap details page. *The YAML detail will be shown on the left sidebar*:

.. image:: ./_static/imgs/screenshots/costmap_page.png
   :align: center

.. |highlight| image:: ./_static/imgs/screenshots/highlight.png
.. |delete| image:: ./_static/imgs/screenshots/delete.png
.. |right| image:: ./_static/imgs/screenshots/right.png
.. |wrong| image:: ./_static/imgs/screenshots/wrong.png
.. |save_btn| image:: ./_static/imgs/screenshots/save_btn.png
.. |download_btn| image:: ./_static/imgs/screenshots/download_btn.png
.. |mouse_coords| image:: ./_static/imgs/screenshots/mouse_coords.png


Edit Marks / Paths / Blocks
---------------------------

.. |zoom_btns| image:: ./_static/imgs/screenshots/zoom_btns.png
.. |click_coords| image:: ./_static/imgs/screenshots/click_coords.png
.. |toggle_axis| image:: ./_static/imgs/screenshots/toggle_axis.png

We could add mark points/paths/blocks using the simple UI. After saving them,
we could get them as :code:`metadata` when downloading the map.

* Zoom in / Zoom out / Zoom reset |zoom_btns| buttons allow you to see details on the map.

* When mouse moves in the map area, the coords in real-world coordinate system will show
  on the top-right of the map |mouse_coords|

* We could also click on the map, the coords of clicked point will be show in popup on the bottom-right
  |click_coords|

* Show / hide axis via |toggle_axis|. The red is :code:`x` axis; the green is :code:`y` axis.

Marks
"""""

.. |draw_mark| image:: ./_static/imgs/screenshots/draw_mark.png

* **Add** new mark point

  * Click |draw_mark| button.
  * Find your mark point position on the map when moving the mouse.
  * Left click the position and **hold & drag** to the expected direction. Then release the mouse.
  * New mark point with its angle will be added on the map locally.

  .. image:: ./_static/imgs/screenshots/mark_sample.png
    :align: center


* **Edit** mark points

  .. image:: ./_static/imgs/screenshots/marks.png
    :align: center

  * Click :code:`Marks` on the left sidebar to show all the marks
  * Click |highlight| to highline the mark on the right map
  * Update the map name on **input field**. The new name will be updated locally
  * Click |delete| to remove the mark locally

* **Save**

  * Do not forget save all updates to the database. Click save button

    .. image:: ./_static/imgs/screenshots/save_btn.png

  * *OR you could save once after marks / paths / blocks are updated.*

Paths
"""""

.. |draw_path| image:: ./_static/imgs/screenshots/draw_path.png

* **Add** new path

  * Click |draw_path| button.
  * Find your positions of path on the map when moving the mouse.
  * Left click the position to add path points one by one.
  * Click |right| to add the new path into the paths locally.
    *(The |right| will enable after adding two points for the path)*
  * Or click |wrong| to remove the new path drawing.

  .. image:: ./_static/imgs/screenshots/path_sample.png
    :align: center


* **Edit** paths

  .. image:: ./_static/imgs/screenshots/paths.png
    :align: center

  * Click :code:`Paths` on the left sidebar to show all the paths
  * Click |highlight| to highline the path on the right map
  * Update the map name on **input field**. The new name will be updated locally
  * Click |delete| to remove the path locally

* **Save**

  * Do not forget save all updates to the database. Click save button

    .. image:: ./_static/imgs/screenshots/save_btn.png

  * *OR you could save once after marks / paths / blocks are updated.*


Blocks
""""""

.. |draw_block| image:: ./_static/imgs/screenshots/draw_block.png

* **Add** new block

  * Click |draw_block| button.
  * Find your corner positions of block on the map when moving the mouse.
  * Left click the position to add block corners one by one.
  * Click |right| to add the new block into the blocks locally.
    *(The |right| will enable after adding one corner for the block)*
  * Or click |wrong| to remove the new block drawing.

  .. image:: ./_static/imgs/screenshots/block_sample.png
    :align: center


* **Edit** blocks

  .. image:: ./_static/imgs/screenshots/blocks.png
    :align: center

  * Click :code:`Blocks` on the left sidebar to show all the blocks
  * Click |highlight| to highline the block on the right map
  * Update the map name on **input field**. The new name will be updated locally
  * Click |delete| to remove the block locally

* **Save**

  * Do not forget save all updates to the database. Click save button

    .. image:: ./_static/imgs/screenshots/save_btn.png

  * *OR you could save once after marks / paths / blocks are updated.*


.. attention:: **Don't forget SAVE**

   Save all updates to the database. Click save button |save_btn|

   *Our new version will save data automatically. It's on the way!*


Edit Map Image
--------------

Edit the image directly on the map image. You don't need to open GIMP again.

*Currently, it's under developing. Coming soon...*


Download Map
------------

Download via site
"""""""""""""""""

* Click |download_btn| on the right side of map details page
* Save :code:`map.zip` to your PC. The :code:`map.zip` includes:

  * :code:`map.png`, the costmap
  * :code:`map.yaml`, the related YAML file of the costmap
  * :code:`metadata.yaml`, the file contains mark points / paths / blocks
    *(don't forget save button!)*


API Fetch Map
"""""""""""""

.. |profile_icon| image:: ./_static/imgs/screenshots/profile_icon.png
.. |access_token_btn| image:: ./_static/imgs/screenshots/access_token_btn.png

* Click :code:`Profile & Token` link under |profile_icon| and land to :code:`Profile & Token` page.
* Click |access_token_btn| button and get the token.
* Download map via our API *(bash code)*

  .. code:: bash

     curl -v -o map.zip -X GET "http://api.motivedge.io/map/MAP_ID/2d?me_token=TOKEN"

  * :code:`MAP_ID` could be found in the map details page.
    *(Next to the map name)*
  * :code:`me_token` is the generated token using above button.
    *(Required field)*

* The fetched map zip file includes :code:`map.yaml`, :code:`map.png` (costmap), and :code:`metadata.yaml`
  (the marks points / paths / blocks). We could unzip the file *(bash code)*:

  .. code:: bash

     unzip map.zip

* Now we could see the map in our system and we could update our robot :code:`map_server` to use this latest map.

.. attention:: **SDK will release soon**

   Our SDK is under developing and will be released soon. We don't need above
   complicated fetch map steps after releasing.

   **Only one line of code will finish above all.**
