Getting Started
---------------

Clustergrammer is a web-based tool for visualizing and analyzing high-dimensional data as interactive and shareable hierarchically clustered heatmaps (see :ref:`intro_heatmap_clustergram` for more information). Clustergrammer can be used in three main ways:

#. :ref:`clustergrammer_web`: `http://amp.pharm.mssm.edu/clustergrammer`_
#. :ref:`clustergrammer_widget`
#. :ref:`clustergrammer_js` and :ref:`clustergrammer_py` libraries

This section will provide information on how to interact with the visualization and how to quickly visualize your own data using the :ref:`clustergrammer_web` and the :ref:`clustergrammer_widget`. See :ref:`case_studies` for examples of how Clustergrammer can be used to explore and analyze real world data. For developers interested in building their own web page using Clustergrammer, please refer to the :ref:`building_web_page` section.

What's New
-----------

JupyterCon 2018
===============

.. raw:: html

         <div style="position: relative; padding-bottom: 10px; height: 0; overflow: hidden; max-width: 100%; height: auto;">

         <iframe width="560" height="315" src="https://www.youtube.com/embed/82epZkmfkrE" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
         </div>

The Clustergrammer-Widget was recently presented at JupyterCon 2018.

Clustergrammer2
===============

.. figure:: _static/clustergrammer2_480px.gif
  :width: 800px
  :align: left
  :alt: demo GIF
  :target: https://github.com/ismms-himc/clustergrammer2-examples

Clustergrammer is currently being re-built using the WebGL library `regl`_:

* :ref:`clustergrammer_gl`: WebGL JavaScript Library
* :ref:`clustergrammer2`: WebGL Jupyter Widget

Try running the Clustergrammer2 Jupyter widget on MyBinder

|intro-notebook|

|ccle-notebook|

and see `Clustergrammer2-Examples`_.

Interacting with Clustergrammer Heatmaps
========================================

.. figure:: _static/demo_high-fr.gif
  :width: 800px
  :align: left
  :alt: demo GIF
  :target: http://amp.pharm.mssm.edu/clustergrammer/viz_sim_mats/58a492b4a63cb826f0be6476/rc_two_cats.txt

Clustergrammer produces highly interactive visualizations that enable intuitive exploration of high-dimensional data including:

- :ref:`zooming_and_panning`
- :ref:`row_col_reordering` (e.g. reorder based on sum)
- :ref:`interactive_dendrogram`
- :ref:`interactive_dim_reduction` (e.g. filter rows based on variance)
- :ref:`interactive_categories`
- :ref:`crop`
- :ref:`row_search`

Press play or interact with the gene-expression demo below to see some of Clustergrammer's interactive features and see :ref:`interacting_with_viz` for more information:

.. raw:: html

   <iframe id='iframe_preview' src="https://amp.pharm.mssm.edu/clustergrammer/demo/" frameBorder="0" style='height: 495px; width:730px; margin-bottom:15px;'></iframe>

Clustergrammer also has :ref:`biology_specific_features` for working with gene-level data including:

- Mouseover gene names and description look-up (using `Harmonizome`_)
- Enrichment analysis to find biological information (e.g. up-stream transcription factors) specific to your set of genes (using `Enrichr`_)


.. _getting_started_web_app:

Clustergrammer Web-App
======================
Users can easily generate an interactive and shareable heatmap visualization using the :ref:`clustergrammer_web` (see upload section screenshot below). Simply upload a tab-separated matrix file (see :ref:`matrix_format_io` for more information) at the `homepage`_ to be redirected to a permanent and shareable visualization of your data.

.. figure:: _static/clustergrammer_web_upload.png
  :width: 550px
  :align: left
  :alt: Clustergrammer Web
  :target: http://amp.pharm.mssm.edu/clustergrammer/

  Users can upload their data using the web app `homepage`_. Simply choose your file and upload to be redirected to your permanent and shareable visualization.

Once you upload your data, the :ref:`clustergrammer_web` clusters your data and produces three views: a heatmap of your input matrix, a similarity matrix of your columns, and a similarity matrix of your rows. See the screenshots below and the `example visualization`_ for an example results page.

**Heatmap View**

.. figure:: _static/web_app_heatmap.png
  :width: 800px
  :align: left
  :alt: Web application heatmap
  :target: http://amp.pharm.mssm.edu/clustergrammer/viz_sim_mats/58a492b4a63cb826f0be6476/rc_two_cats.txt

  Above is an example clustergram visualization produced by the :ref:`clustergrammer_web`. Clustergrammer produces three views of your data; the clustered heatmap view is shown above.

**Similarity Matrix View**

.. figure:: _static/web_app_sim_mat.png
  :width: 800px
  :align: left
  :alt: Web application sim-mat
  :target: http://amp.pharm.mssm.edu/clustergrammer/viz_sim_mats/58a492b4a63cb826f0be6476/rc_two_cats.txt

  Clustergrammer produces similarity matrices of rows and columns to provide additional perspectives on your data. Above is an example column similarity matrix.

Users can share their interactive visualizations using their permanent link. See :ref:`interacting_with_viz` for more information.

.. _getting_started_widget:

Clustergrammer-Widget
=====================
`Jupyter`_ notebooks are ideal for generating reproducible workflows and analysis. They are also the best way to share Clustergrammer's interactive visualizations while providing context, analysis, and the underlying data to enable reproducibility (see :ref:`clustergrammer_widget_examples`). The :ref:`clustergrammer_widget` enables users to easily produce interactive visualizations within a Jupyter notebook that can be shared with collaborators (using `nbviewer`_). The :ref:`clustergrammer_widget` can be used to visualize a matrix of data from a matrix file or from a `Pandas`_ DataFrame (see :ref:`matrix_format_io` for more information).

Clustergrammer has been applied to visualize and analyze a wide variety of biological and non-biological data. See the Jupyter notebook examples below and :ref:`case_studies` for more information:

- `Running_clustergrammer_widget.ipynb`_
- `DataFrame_Example.ipynb`_
- `CCLE Jupyter Notebook`_
- `Lung Cancer PTM and Gene Expression Regulation`_
- `Single-Cell CyTOF Data`_
- `MNIST Notebook`_
- `USDA Nutrient Dataset`_
- `Iris Dataset.ipynb`_


To use the :ref:`clustergrammer_widget` users need to install: `Python`_, `Jupyter`_ notebook, the widget dependencies (see :ref:`clustergrammer_widget_dependencies`), and `ipywidgets`_ version >6.0.0 (required for saving notebook with widgets). Users can `install Anaconda`_, a Python distribution that includes the Jupyter notebook as well as other scientific computing libraries, to easily obtain the necessary dependencies (except ipywidgets version >6.0.0). Once these requirements have been met, ``clustergrammer_widget`` can then be installed (with pip) and enabled using the following commands:
::

  pip install --upgrade clustergrammer_widget
  jupyter nbextension enable --py --sys-prefix widgetsnbextension
  jupyter nbextension enable --py --sys-prefix clustergrammer_widget

With the ``clustergrammer_widget`` installed and enabled users can visualize their data (from a file) using the following Python commands:
::

  # import clustergrammer_widgets and initialize network object
  from clustergrammer_widget import *
  net = Network(clustergrammer_widget)

  # load matrix file and cluster using default parameters
  net.load_file('rc_two_cats.txt')
  net.cluster()

  # make interactive widget
  net.widget()

See the screenshot below for an example widget visualization:

.. figure:: _static/jupyter_widget_nbviewer.png
  :width: 900px
  :align: left
  :alt: Jupyter Widget NBViewer
  :target: http://nbviewer.jupyter.org/github/MaayanLab/clustergrammer-widget/blob/master/Running_clustergrammer_widget.ipynb

  Clustergrammer can be used as an interactive widget within a Jupyter notebook and shared using nbviewer (see `Running_clustergrammer_widget.ipynb`_ example).

Users can download and reproduce the example notebook, `Running_clustergrammer_widget.ipynb`_, by cloning its `GitHub repo`_. For more information about using the widget (e.g. visualizing data from a Pandas DataFrame and sharing notebooks) see :ref:`clustergrammer_widget`.


.. _`Clustergrammer2-Examples`: https://github.com/ismms-himc/clustergrammer2-examples
.. _`Clustergrammer2`: https://github.com/ismms-himc/clustergrammer2
.. _`regl`: http://regl.party/
.. _`example visualization`: http://amp.pharm.mssm.edu/clustergrammer/viz_sim_mats/58a492b4a63cb826f0be6476/rc_two_cats.txt
.. _`Enrichr`: http://amp.pharm.mssm.edu/Enrichr/
.. _`Harmonizome`: http://amp.pharm.mssm.edu/Harmonizome/
.. _`homepage`: http://amp.pharm.mssm.edu/clustergrammer/
.. _`Jupyter`: http://jupyter.org/
.. _`nbviewer`: http://nbviewer.jupyter.org/
.. _`Pandas`: http://pandas.pydata.org/
.. _`Python`: https://www.python.org/
.. _`ipywidgets`: http://ipywidgets.readthedocs.io/en/latest/
.. _`GitHub repo`: https://github.com/MaayanLab/clustergrammer-widget
.. _`http://amp.pharm.mssm.edu/clustergrammer`: http://amp.pharm.mssm.edu/clustergrammer/
.. _`install Anaconda`: https://www.continuum.io/downloads

.. _`Running_clustergrammer_widget.ipynb`: http://nbviewer.jupyter.org/github/MaayanLab/clustergrammer-widget/blob/master/Running_clustergrammer_widget.ipynb

.. _`DataFrame_Example.ipynb`: http://nbviewer.jupyter.org/github/MaayanLab/clustergrammer-widget/blob/master/DataFrame_Example.ipynb

.. _`Lung Cancer PTM and Gene Expression Regulation`: http://nbviewer.jupyter.org/github/MaayanLab/CST_Lung_Cancer_Viz/blob/master/notebooks/CST_Data_Viz.ipynb

.. _`Single-Cell CyTOF Data`: http://nbviewer.jupyter.org/github/MaayanLab/Cytof_Plasma_PMA/blob/master/notebooks/Plasma_vs_PMA_Phosphorylation.ipynb

.. _`Iris Dataset.ipynb`: http://nbviewer.jupyter.org/github/MaayanLab/iris_clustergrammer_visualization/blob/master/Iris%20Dataset.ipynb

.. _`CCLE Jupyter Notebook`: http://nbviewer.jupyter.org/github/MaayanLab/CCLE_Clustergrammer/blob/master/notebooks/Clustergrammer_CCLE_Notebook.ipynb

.. _`MNIST Notebook`: http://nbviewer.jupyter.org/github/MaayanLab/MNIST_heatmaps/blob/master/notebooks/MNIST_Notebook.ipynb

.. _`USDA Nutrient Dataset`: http://nbviewer.jupyter.org/github/MaayanLab/USDA_Nutrients_Viz/blob/master/USDA_Nutrients.ipynb

.. |intro-notebook| image:: https://img.shields.io/badge/launch-1.0%20Example%20notebook-579ACA.svg?logo=data:image/png;base64,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
    :alt: version
    :target: https://mybinder.org/v2/gh/ismms-himc/clustergrammer2-examples/master?filepath=notebooks%2F1.0_Clustergrammer2_Example_Notebook.ipynb

.. |ccle-notebook| image:: https://img.shields.io/badge/launch-2.0%20CCLE%20Gene%20Expression-579ACA.svg?logo=data:image/png;base64,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
    :alt: version
    :target: https://mybinder.org/v2/gh/ismms-himc/clustergrammer2_examples/master?filepath=notebooks%2F2.0_CCLE_Gene_Expression.ipynb
