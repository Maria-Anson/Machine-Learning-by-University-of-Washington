# Fire up Turi Create

We always start with this line before using any part of Turi Create


```python
import turicreate
```

# Load a tabular data set


```python
sf = turicreate.SFrame('people-example.csv')
```


<pre>Finished parsing file /home/anson/Course/Week 1/people-example.csv</pre>



<pre>Parsing completed. Parsed 7 lines in 0.081499 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[str,str,str,int]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------



<pre>Finished parsing file /home/anson/Course/Week 1/people-example.csv</pre>



<pre>Parsing completed. Parsed 7 lines in 0.063211 secs.</pre>


# SFrame basics


```python
sf #we can view first few lines of table
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>




```python
sf.head()
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>




```python
sf.tail()  # view end of the table
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>



# Turi Create visualization


```python
# .show() visualizes any data structure in Turi Create
sf.show()
```


<pre>Materializing SFrame</pre>



<html>                 <body>                     <iframe style="border:0;margin:0" width="1000" height="1500" srcdoc='<html lang="en">                         <head>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega/5.4.0/vega.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/4.0.0/vega-embed.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.js"></script>                             <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.css">                             <style>                             .vega-actions > a{                                 color:white;                                 text-decoration: none;                                 font-family: "Arial";                                 cursor:pointer;                                 padding:5px;                                 background:#AAAAAA;                                 border-radius:4px;                                 padding-left:10px;                                 padding-right:10px;                                 margin-right:5px;                             }                             .vega-actions{                                 margin-top:20px;                                 text-align:center                             }                            .vega-actions > a{                                 background:#999999;                            }                             </style>                         </head>                         <body>                             <div id="vis">                             </div>                             <script>                                 var vega_json = "{\"$schema\": \"https://vega.github.io/schema/vega/v4.json\", \"metadata\": {\"bubbleOpts\": {\"showAllFields\": false, \"fields\": [{\"field\": \"left\"}, {\"field\": \"right\"}, {\"field\": \"count\"}, {\"field\": \"label\"}]}}, \"width\": 800, \"height\": 1280, \"padding\": 8, \"data\": [{\"name\": \"pts_store\"}, {\"name\": \"source_2\", \"values\": [{\"a\": 0, \"title\": \"First Name\", \"num_row\": 7, \"type\": \"str\", \"num_unique\": 7, \"num_missing\": 0, \"categorical\": [{\"label\": \"Alex\", \"label_idx\": 0, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Alice\", \"label_idx\": 1, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Bob\", \"label_idx\": 2, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Derek\", \"label_idx\": 3, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Felix\", \"label_idx\": 4, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Malcolm\", \"label_idx\": 5, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Tod\", \"label_idx\": 6, \"count\": 1, \"percentage\": \"14.2857%\"}], \"numeric\": []}, {\"a\": 1, \"title\": \"Last Name\", \"num_row\": 7, \"type\": \"str\", \"num_unique\": 7, \"num_missing\": 0, \"categorical\": [{\"label\": \"Brown\", \"label_idx\": 0, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Campbell\", \"label_idx\": 1, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Cooper\", \"label_idx\": 2, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Jone\", \"label_idx\": 3, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Smith\", \"label_idx\": 4, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Ward\", \"label_idx\": 5, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Williams\", \"label_idx\": 6, \"count\": 1, \"percentage\": \"14.2857%\"}], \"numeric\": []}, {\"a\": 2, \"title\": \"Country\", \"num_row\": 7, \"type\": \"str\", \"num_unique\": 6, \"num_missing\": 0, \"categorical\": [{\"label\": \"United States\", \"label_idx\": 0, \"count\": 2, \"percentage\": \"28.5714%\"}, {\"label\": \"Canada\", \"label_idx\": 1, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"England\", \"label_idx\": 2, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Poland\", \"label_idx\": 3, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Switzerland\", \"label_idx\": 4, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"USA\", \"label_idx\": 5, \"count\": 1, \"percentage\": \"14.2857%\"}], \"numeric\": []}, {\"a\": 3, \"title\": \"age\", \"num_row\": 7, \"type\": \"integer\", \"num_unique\": 4, \"num_missing\": 0, \"mean\": 23.142857, \"min\": 22.0, \"max\": 25.0, \"median\": 23.0, \"stdev\": 0.989743, \"numeric\": [{\"left\": 14, \"right\": 15, \"count\": 0}, {\"left\": 15, \"right\": 16, \"count\": 0}, {\"left\": 16, \"right\": 17, \"count\": 0}, {\"left\": 17, \"right\": 18, \"count\": 0}, {\"left\": 18, \"right\": 19, \"count\": 0}, {\"left\": 19, \"right\": 20, \"count\": 0}, {\"left\": 20, \"right\": 21, \"count\": 0}, {\"left\": 21, \"right\": 22, \"count\": 0}, {\"left\": 22, \"right\": 23, \"count\": 2}, {\"left\": 23, \"right\": 24, \"count\": 3}, {\"left\": 24, \"right\": 25, \"count\": 1}, {\"left\": 25, \"right\": 26, \"count\": 1}, {\"left\": 26, \"right\": 27, \"count\": 0}, {\"left\": 27, \"right\": 28, \"count\": 0}, {\"left\": 28, \"right\": 29, \"count\": 0}, {\"left\": 29, \"right\": 30, \"count\": 0}, {\"left\": 30, \"right\": 31, \"count\": 0}, {\"left\": 31, \"right\": 32, \"count\": 0}, {\"left\": 32, \"right\": 33, \"count\": 0}, {\"left\": 33, \"right\": 34, \"count\": 0}, {\"start\": 14, \"stop\": 34, \"step\": 1}], \"categorical\": []}]}, {\"name\": \"data_2\", \"source\": \"source_2\", \"transform\": [{\"type\": \"formula\", \"expr\": \"20\", \"as\": \"c_x_axis_back\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+66\", \"as\": \"c_main_background\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+43\", \"as\": \"c_top_bar\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+59\", \"as\": \"c_top_title\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+58\", \"as\": \"c_top_type\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+178\", \"as\": \"c_rule\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+106\", \"as\": \"c_num_rows\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+130\", \"as\": \"c_num_unique\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+154\", \"as\": \"c_missing\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+105\", \"as\": \"c_num_rows_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+130\", \"as\": \"c_num_unique_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+154\", \"as\": \"c_missing_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+195\", \"as\": \"c_frequent_items\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+218\", \"as\": \"c_first_item\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+235\", \"as\": \"c_second_item\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+252\", \"as\": \"c_third_item\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+269\", \"as\": \"c_fourth_item\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+286\", \"as\": \"c_fifth_item\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+200\", \"as\": \"c_mean\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+220\", \"as\": \"c_min\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+240\", \"as\": \"c_max\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+260\", \"as\": \"c_median\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+280\", \"as\": \"c_stdev\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+198\", \"as\": \"c_mean_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+218\", \"as\": \"c_min_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+238\", \"as\": \"c_max_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+258\", \"as\": \"c_median_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+278\", \"as\": \"c_stdev_val\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+106\", \"as\": \"graph_offset\"}, {\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"a\\\"])*300+132\", \"as\": \"graph_offset_categorical\"}, {\"type\": \"formula\", \"expr\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?false:true\", \"as\": \"c_clip_val\"}, {\"type\": \"formula\", \"expr\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?250:0\", \"as\": \"c_width_numeric_val\"}, {\"type\": \"formula\", \"expr\": \"(toString(datum[\\\"type\\\"]) == \\\"str\\\")?false:true\", \"as\": \"c_clip_val_cat\"}, {\"type\": \"formula\", \"expr\": \"(toString(datum[\\\"type\\\"]) == \\\"str\\\")?250:0\", \"as\": \"c_width_numeric_val_cat\"}]}], \"marks\": [{\"encode\": {\"enter\": {\"x\": {\"value\": 0}, \"width\": {\"value\": 734}, \"y\": {\"value\": 0}, \"height\": {\"value\": 366}, \"clip\": {\"value\": 0}, \"fill\": {\"value\": \"#ffffff\"}, \"fillOpacity\": {\"value\": 0}, \"stroke\": {\"value\": \"#000000\"}, \"strokeWidth\": {\"value\": 0}}}, \"marks\": [{\"encode\": {\"enter\": {\"x\": {\"value\": 0}, \"width\": {\"value\": 734}, \"y\": {\"value\": 0}, \"height\": {\"value\": 366}, \"clip\": {\"value\": 0}, \"fill\": {\"value\": \"#ffffff\"}, \"fillOpacity\": {\"value\": 0}, \"stroke\": {\"value\": \"#000000\"}, \"strokeWidth\": {\"value\": 0}}}, \"scales\": [], \"axes\": [], \"marks\": [{\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 33}, \"width\": {\"value\": 700}, \"y\": {\"value\": 66}, \"height\": {\"value\": 250}, \"fill\": {\"value\": \"#FEFEFE\"}, \"fillOpacity\": {\"value\": 1}, \"stroke\": {\"value\": \"#DEDEDE\"}, \"strokeWidth\": {\"value\": 0.5}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]\"}, \"y\": {\"field\": \"c_main_background\"}}}, \"type\": \"rect\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 33}, \"width\": {\"value\": 700}, \"y\": {\"value\": 43}, \"height\": {\"value\": 30}, \"fill\": {\"value\": \"#F5F5F5\"}, \"fillOpacity\": {\"value\": 1}, \"stroke\": {\"value\": \"#DEDEDE\"}, \"strokeWidth\": {\"value\": 0.5}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]\"}, \"y\": {\"field\": \"c_top_bar\"}}}, \"type\": \"rect\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 720}, \"y\": {\"value\": 58}, \"text\": {\"signal\": \"&apos;&apos;+datum[\\\"type\\\"]\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#595859\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+687\"}, \"y\": {\"field\": \"c_top_type\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 44}, \"y\": {\"value\": 59}, \"text\": {\"signal\": \"&apos;&apos;+datum[\\\"title\\\"]\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 15}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#9B9B9B\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+11\"}, \"y\": {\"field\": \"c_top_title\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 178}, \"stroke\": {\"value\": \"#EDEDEB\"}, \"strokeWidth\": {\"value\": 1}, \"strokeCap\": {\"value\": \"butt\"}, \"x2\": {\"value\": 720}, \"y2\": {\"value\": 178}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"x2\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+687\"}, \"y\": {\"field\": \"c_rule\"}, \"y2\": {\"field\": \"c_rule\"}}}, \"type\": \"rule\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 106}, \"text\": {\"value\": \"Num. Rows:\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_num_rows\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 130}, \"text\": {\"value\": \"Num. Unique:\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_num_unique\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 154}, \"text\": {\"value\": \"Missing:\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_missing\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 105}, \"text\": {\"signal\": \"toString(format(datum[\\\"num_row\\\"], \\\",\\\"))\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#5A5A5A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_num_rows_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 130}, \"text\": {\"signal\": \"toString(format(datum[\\\"num_unique\\\"], \\\",\\\"))\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#5A5A5A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_num_unique_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 154}, \"text\": {\"signal\": \"toString(format(datum[\\\"num_missing\\\"], \\\",\\\"))\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 12}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#5A5A5A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_missing_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"str\\\")? \\\"Frequent Items\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_frequent_items\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 520}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 1) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][0][\\\"label\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+487\"}, \"y\": {\"field\": \"c_first_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 520}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 2) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][1][\\\"label\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+487\"}, \"y\": {\"field\": \"c_second_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 520}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 3) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][2][\\\"label\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+487\"}, \"y\": {\"field\": \"c_third_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 520}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 4) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][3][\\\"label\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+487\"}, \"y\": {\"field\": \"c_fourth_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 520}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 5) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][4][\\\"label\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+487\"}, \"y\": {\"field\": \"c_fifth_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 1) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][0][\\\"count\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#7A7A7A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_first_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 2) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][1][\\\"count\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#7A7A7A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_second_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 3) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][2][\\\"count\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#7A7A7A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_third_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 4) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][3][\\\"count\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#7A7A7A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_fourth_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"((datum[\\\"categorical\\\"].length >= 5) &amp;&amp; (toString(datum[\\\"type\\\"]) == \\\"str\\\"))? toString(datum[\\\"categorical\\\"][4][\\\"count\\\"]):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#7A7A7A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_fifth_item\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 200}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")? \\\"Mean:\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"clip\": {\"value\": true}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_mean\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 220}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")? \\\"Min:\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_min\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 240}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")? \\\"Max:\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_max\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 260}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")? \\\"Median:\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_median\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 500}, \"y\": {\"value\": 280}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")? \\\"St. Dev:\\\":\\\"\\\"\"}, \"align\": {\"value\": \"left\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 11}, \"fontWeight\": {\"value\": \"bold\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#4A4A4A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+467\"}, \"y\": {\"field\": \"c_stdev\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 198}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?toString(format(datum[\\\"mean\\\"], \\\",\\\")):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#6A6A6A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_mean_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 218}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?toString(format(datum[\\\"min\\\"], \\\",\\\")):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#6A6A6A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_min_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 238}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?toString(format(datum[\\\"max\\\"], \\\",\\\")):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#6A6A6A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_max_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 258}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?toString(format(datum[\\\"median\\\"], \\\",\\\")):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#6A6A6A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_median_val\"}}}, \"type\": \"text\"}, {\"from\": {\"data\": \"data_2\"}, \"encode\": {\"enter\": {\"x\": {\"value\": 700}, \"y\": {\"value\": 278}, \"text\": {\"signal\": \"(toString(datum[\\\"type\\\"]) == \\\"integer\\\" || toString(datum[\\\"type\\\"]) == \\\"float\\\")?toString(format(datum[\\\"stdev\\\"], \\\",\\\")):\\\"\\\"\"}, \"align\": {\"value\": \"right\"}, \"baseline\": {\"value\": \"middle\"}, \"dx\": {\"value\": 0, \"offset\": 0}, \"dy\": {\"value\": 0, \"offset\": 0}, \"angle\": {\"value\": 0}, \"font\": {\"value\": \"AvenirNext-Medium\"}, \"fontSize\": {\"value\": 10}, \"fontWeight\": {\"value\": \"normal\"}, \"fontStyle\": {\"value\": \"normal\"}, \"fill\": {\"value\": \"#6A6A6A\"}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+667\"}, \"y\": {\"field\": \"c_stdev_val\"}}}, \"type\": \"text\"}, {\"from\": {\"facet\": {\"name\": \"new_data\", \"data\": \"data_2\", \"field\": \"numeric\"}}, \"encode\": {\"enter\": {\"x\": {\"value\": 120}, \"width\": {\"value\": 250}, \"y\": {\"field\": \"graph_offset\"}, \"height\": {\"value\": 150}, \"fill\": {\"value\": \"#ffffff\"}, \"fillOpacity\": {\"value\": 0}, \"stroke\": {\"value\": \"#000000\"}, \"strokeWidth\": {\"value\": 0}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+87\"}, \"clip\": {\"field\": \"c_clip_val\"}, \"width\": {\"field\": \"c_width_numeric_val\"}}}, \"type\": \"group\", \"scales\": [{\"name\": \"x\", \"type\": \"linear\", \"domain\": {\"data\": \"new_data\", \"fields\": [\"left\", \"right\"], \"sort\": true}, \"range\": [0, {\"signal\": \"width\"}], \"nice\": true, \"zero\": true}, {\"name\": \"y\", \"type\": \"linear\", \"domain\": {\"data\": \"new_data\", \"field\": \"count\"}, \"range\": [{\"signal\": \"height\"}, 0], \"nice\": true, \"zero\": true}], \"axes\": [{\"title\": \"Values\", \"scale\": \"x\", \"labelOverlap\": true, \"orient\": \"bottom\", \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"zindex\": 1}, {\"scale\": \"x\", \"domain\": false, \"grid\": true, \"labels\": false, \"maxExtent\": 0, \"minExtent\": 0, \"orient\": \"bottom\", \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"ticks\": false, \"zindex\": 0, \"gridScale\": \"y\"}, {\"title\": \"Count\", \"scale\": \"y\", \"labelOverlap\": true, \"orient\": \"left\", \"tickCount\": {\"signal\": \"ceil(height/40)\"}, \"zindex\": 1}, {\"scale\": \"y\", \"domain\": false, \"grid\": true, \"labels\": false, \"maxExtent\": 0, \"minExtent\": 0, \"orient\": \"left\", \"tickCount\": {\"signal\": \"ceil(height/40)\"}, \"ticks\": false, \"zindex\": 0, \"gridScale\": \"x\"}], \"style\": \"cell\", \"signals\": [{\"name\": \"width\", \"update\": \"250\"}, {\"name\": \"height\", \"update\": \"150\"}], \"marks\": [{\"name\": \"marks\", \"type\": \"rect\", \"style\": [\"rect\"], \"from\": {\"data\": \"new_data\"}, \"encode\": {\"hover\": {\"fill\": {\"value\": \"#7EC2F3\"}}, \"update\": {\"x\": {\"scale\": \"x\", \"field\": \"left\"}, \"x2\": {\"scale\": \"x\", \"field\": \"right\"}, \"y\": {\"scale\": \"y\", \"field\": \"count\"}, \"y2\": {\"scale\": \"y\", \"value\": 0}, \"fill\": {\"value\": \"#108EE9\"}}}}]}, {\"from\": {\"facet\": {\"name\": \"data_5\", \"data\": \"data_2\", \"field\": \"categorical\"}}, \"encode\": {\"enter\": {\"x\": {\"value\": 170}, \"width\": {\"value\": 250}, \"y\": {\"field\": \"graph_offset_categorical\"}, \"height\": {\"value\": 150}, \"fill\": {\"value\": \"#ffffff\"}, \"fillOpacity\": {\"value\": 0}, \"stroke\": {\"value\": \"#000000\"}, \"strokeWidth\": {\"value\": 0}}, \"update\": {\"x\": {\"signal\": \"datum[\\\"c_x_axis_back\\\"]+137\"}, \"clip\": {\"field\": \"c_clip_val_cat\"}, \"width\": {\"field\": \"c_width_numeric_val_cat\"}}}, \"type\": \"group\", \"style\": \"cell\", \"signals\": [{\"name\": \"unit\", \"value\": {}, \"on\": [{\"events\": \"mousemove\", \"update\": \"isTuple(group()) ? group() : unit\"}]}, {\"name\": \"pts\", \"update\": \"data(\\\"pts_store\\\").length &amp;&amp; {count: data(\\\"pts_store\\\")[0].values[0]}\"}, {\"name\": \"pts_tuple\", \"value\": {}, \"on\": [{\"events\": [{\"source\": \"scope\", \"type\": \"click\"}], \"update\": \"datum &amp;&amp; item().mark.marktype !== &apos;group&apos; ? {unit: \\\"\\\", encodings: [\\\"x\\\"], fields: [\\\"count\\\"], values: [datum[\\\"count\\\"]]} : null\", \"force\": true}]}, {\"name\": \"pts_modify\", \"on\": [{\"events\": {\"signal\": \"pts_tuple\"}, \"update\": \"modify(\\\"pts_store\\\", pts_tuple, true)\"}]}], \"marks\": [{\"name\": \"marks\", \"type\": \"rect\", \"style\": [\"bar\"], \"from\": {\"data\": \"data_5\"}, \"encode\": {\"hover\": {\"fill\": {\"value\": \"#7EC2F3\"}}, \"update\": {\"x\": {\"scale\": \"x\", \"field\": \"count\"}, \"x2\": {\"scale\": \"x\", \"value\": 0}, \"y\": {\"scale\": \"y\", \"field\": \"label\"}, \"height\": {\"scale\": \"y\", \"band\": true}, \"fill\": {\"value\": \"#108EE9\"}}}}], \"scales\": [{\"name\": \"x\", \"type\": \"linear\", \"domain\": {\"data\": \"data_5\", \"field\": \"count\"}, \"range\": [0, 250], \"nice\": true, \"zero\": true}, {\"name\": \"y\", \"type\": \"band\", \"domain\": {\"data\": \"data_5\", \"field\": \"label\", \"sort\": {\"op\": \"mean\", \"field\": \"label_idx\", \"order\": \"descending\"}}, \"range\": [150, 0], \"paddingInner\": 0.1, \"paddingOuter\": 0.05}], \"axes\": [{\"orient\": \"top\", \"scale\": \"x\", \"labelOverlap\": true, \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"title\": \"Count\", \"zindex\": 1}, {\"orient\": \"top\", \"scale\": \"x\", \"domain\": false, \"grid\": true, \"labels\": false, \"maxExtent\": 0, \"minExtent\": 0, \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"ticks\": false, \"zindex\": 0, \"gridScale\": \"y\"}, {\"scale\": \"y\", \"labelOverlap\": true, \"orient\": \"left\", \"title\": \"Label\", \"zindex\": 1}]}], \"type\": \"group\"}], \"type\": \"group\"}], \"config\": {\"axis\": {\"labelFont\": \"HelveticaNeue-Light, Arial\", \"labelFontSize\": 7, \"labelPadding\": 10, \"labelColor\": \"#595959\", \"titleFont\": \"HelveticaNeue-Light, Arial\", \"titleFontWeight\": \"normal\", \"titlePadding\": 9, \"titleFontSize\": 12, \"titleColor\": \"#595959\"}, \"axisY\": {\"minExtent\": 30}, \"style\": {\"rect\": {\"stroke\": \"rgba(200, 200, 200, 0.5)\"}, \"group-title\": {\"fontSize\": 20, \"font\": \"HelveticaNeue-Light, Arial\", \"fontWeight\": \"normal\", \"fill\": \"#595959\"}}}}";                                 var vega_json_parsed = JSON.parse(vega_json);                                 var toolTipOpts = {                                     showAllFields: true                                 };                                 if(vega_json_parsed["metadata"] != null){                                     if(vega_json_parsed["metadata"]["bubbleOpts"] != null){                                         toolTipOpts = vega_json_parsed["metadata"]["bubbleOpts"];                                     };                                 };                                 vegaEmbed("#vis", vega_json_parsed).then(function (result) {                                     vegaTooltip.vega(result.view, toolTipOpts);                                  });                             </script>                         </body>                     </html>' src="demo_iframe_srcdoc.htm">                         <p>Your browser does not support iframes.</p>                     </iframe>                 </body>             </html>



```python
sf['age'].show()
```


<pre>Materializing SArray</pre>



<html>                 <body>                     <iframe style="border:0;margin:0" width="920" height="770" srcdoc='<html lang="en">                         <head>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega/5.4.0/vega.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/4.0.0/vega-embed.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.js"></script>                             <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.css">                             <style>                             .vega-actions > a{                                 color:white;                                 text-decoration: none;                                 font-family: "Arial";                                 cursor:pointer;                                 padding:5px;                                 background:#AAAAAA;                                 border-radius:4px;                                 padding-left:10px;                                 padding-right:10px;                                 margin-right:5px;                             }                             .vega-actions{                                 margin-top:20px;                                 text-align:center                             }                            .vega-actions > a{                                 background:#999999;                            }                             </style>                         </head>                         <body>                             <div id="vis">                             </div>                             <script>                                 var vega_json = "{\"$schema\": \"https://vega.github.io/schema/vega/v4.json\", \"description\": \"A simple bar chart with embedded data.\", \"autosize\": {\"type\": \"fit\", \"resize\": false, \"contains\": \"padding\"}, \"width\": 720, \"height\": 550, \"padding\": 8, \"title\": \"Distribution of Values [integer]\", \"style\": \"cell\", \"signals\": [{\"name\": \"bins\", \"update\": \"data(\\\"bins_data\\\")[0]\"}, {\"name\": \"binCount\", \"update\": \"(bins.stop - bins.start) / bins.step\"}, {\"name\": \"nullGap\", \"update\": \"data(\\\"nulls\\\").length ? 10 : 0\"}, {\"name\": \"barStep\", \"update\": \"(width - nullGap) / (1 + binCount)\"}], \"data\": [{\"name\": \"source_2\", \"values\": [{\"left\": 14, \"right\": 15, \"count\": 0}, {\"left\": 15, \"right\": 16, \"count\": 0}, {\"left\": 16, \"right\": 17, \"count\": 0}, {\"left\": 17, \"right\": 18, \"count\": 0}, {\"left\": 18, \"right\": 19, \"count\": 0}, {\"left\": 19, \"right\": 20, \"count\": 0}, {\"left\": 20, \"right\": 21, \"count\": 0}, {\"left\": 21, \"right\": 22, \"count\": 0}, {\"left\": 22, \"right\": 23, \"count\": 2}, {\"left\": 23, \"right\": 24, \"count\": 3}, {\"left\": 24, \"right\": 25, \"count\": 1}, {\"left\": 25, \"right\": 26, \"count\": 1}, {\"left\": 26, \"right\": 27, \"count\": 0}, {\"left\": 27, \"right\": 28, \"count\": 0}, {\"left\": 28, \"right\": 29, \"count\": 0}, {\"left\": 29, \"right\": 30, \"count\": 0}, {\"left\": 30, \"right\": 31, \"count\": 0}, {\"left\": 31, \"right\": 32, \"count\": 0}, {\"left\": 32, \"right\": 33, \"count\": 0}, {\"left\": 33, \"right\": 34, \"count\": 0}, {\"start\": 14, \"stop\": 34, \"step\": 1}]}, {\"name\": \"counts\", \"source\": \"source_2\", \"transform\": [{\"type\": \"filter\", \"expr\": \"datum[\\\"missing\\\"] !== true &amp;&amp; datum[\\\"count\\\"] != null\"}]}, {\"name\": \"nulls\", \"source\": \"source_2\", \"transform\": [{\"expr\": \"datum[\\\"missing\\\"] === true &amp;&amp; datum[\\\"count\\\"] != null\", \"type\": \"filter\"}]}, {\"name\": \"bins_data\", \"source\": \"source_2\", \"transform\": [{\"expr\": \"datum[\\\"start\\\"] != null &amp;&amp; datum[\\\"stop\\\"] != null &amp;&amp; datum[\\\"step\\\"] != null\", \"type\": \"filter\"}]}], \"marks\": [{\"type\": \"rect\", \"from\": {\"data\": \"counts\"}, \"encode\": {\"update\": {\"x\": {\"scale\": \"xscale\", \"field\": \"left\", \"offset\": 1}, \"x2\": {\"scale\": \"xscale\", \"field\": \"right\"}, \"y\": {\"scale\": \"yscale\", \"field\": \"count\"}, \"y2\": {\"scale\": \"yscale\", \"value\": 0}, \"fill\": {\"value\": \"#108EE9\"}}, \"hover\": {\"fill\": {\"value\": \"#7EC2F3\"}}}}, {\"type\": \"rect\", \"from\": {\"data\": \"nulls\"}, \"encode\": {\"update\": {\"x\": {\"scale\": \"xscale-null\", \"value\": null, \"offset\": 1}, \"x2\": {\"scale\": \"xscale-null\", \"band\": 1}, \"y\": {\"scale\": \"yscale\", \"field\": \"count\"}, \"y2\": {\"scale\": \"yscale\", \"value\": 0}, \"fill\": {\"value\": \"#108EE9\"}}, \"hover\": {\"fill\": {\"value\": \"#7EC2F3\"}}}}], \"scales\": [{\"name\": \"yscale\", \"type\": \"linear\", \"range\": \"height\", \"round\": true, \"nice\": true, \"domain\": {\"fields\": [{\"data\": \"counts\", \"field\": \"count\"}, {\"data\": \"nulls\", \"field\": \"count\"}]}}, {\"name\": \"xscale\", \"type\": \"linear\", \"range\": [{\"signal\": \"nullGap ? barStep + nullGap : 0\"}, {\"signal\": \"width\"}], \"round\": true, \"domain\": {\"signal\": \"[bins.start, bins.stop]\"}, \"bins\": {\"signal\": \"bins\"}}, {\"name\": \"xscale-null\", \"type\": \"band\", \"range\": [{\"signal\": \"nullGap ? 0 : 1\"}, {\"signal\": \"nullGap ? barStep : 0\"}], \"round\": true, \"domain\": [{\"signal\": \"nullGap ? null : &apos;&apos;\"}]}], \"axes\": [{\"title\": \"Values\", \"orient\": \"bottom\", \"scale\": \"xscale\", \"tickMinStep\": 1, \"grid\": true}, {\"orient\": \"bottom\", \"scale\": \"xscale-null\"}, {\"title\": \"Count\", \"orient\": \"left\", \"scale\": \"yscale\", \"tickCount\": 5, \"offset\": {\"signal\": \"nullGap ? 5 : 0\"}, \"grid\": true}], \"config\": {\"axis\": {\"gridColor\": \"rgba(204,204,204,1.0)\", \"labelFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"labelFontSize\": 12, \"labelPadding\": 10, \"labelColor\": \"rgba(0,0,0,0.847)\", \"tickColor\": \"rgb(136,136,136)\", \"titleFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"titleFontWeight\": \"normal\", \"titlePadding\": 20, \"titleFontSize\": 14, \"titleColor\": \"rgba(0,0,0,0.847)\"}, \"axisY\": {\"minExtent\": 30}, \"legend\": {\"labelFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"labelColor\": \"rgba(0,0,0,0.847)\", \"titleFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"cornerRadius\": 30, \"gradientLength\": 608, \"titleColor\": \"rgba(0,0,0,0.847)\"}, \"range\": {\"heatmap\": {\"scheme\": \"greenblue\"}}, \"style\": {\"rect\": {\"stroke\": \"rgba(200, 200, 200, 0.5)\"}, \"cell\": {\"stroke\": \"transparent\"}, \"group-title\": {\"fontSize\": 29, \"font\": \"HelveticaNeue, Arial\", \"fontWeight\": \"normal\", \"fill\": \"rgba(0,0,0,0.65)\"}}, \"title\": {\"color\": \"rgba(0,0,0,0.847)\", \"font\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"fontSize\": 18, \"fontWeight\": \"normal\", \"offset\": 30}}}";                                 var vega_json_parsed = JSON.parse(vega_json);                                 var toolTipOpts = {                                     showAllFields: true                                 };                                 if(vega_json_parsed["metadata"] != null){                                     if(vega_json_parsed["metadata"]["bubbleOpts"] != null){                                         toolTipOpts = vega_json_parsed["metadata"]["bubbleOpts"];                                     };                                 };                                 vegaEmbed("#vis", vega_json_parsed).then(function (result) {                                     vegaTooltip.vega(result.view, toolTipOpts);                                  });                             </script>                         </body>                     </html>' src="demo_iframe_srcdoc.htm">                         <p>Your browser does not support iframes.</p>                     </iframe>                 </body>             </html>


# Inspect columns of dataset


```python
sf['Country']
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'USA', 'Poland', 'United States', 'Switzerland']




```python
sf['age']
```




    dtype: int
    Rows: 7
    [24, 23, 22, 23, 23, 22, 25]



Some simple columnar operations


```python
sf['age'].mean()
```




    23.142857142857146




```python
sf['age'].max()
```




    25



# Create new columns in our SFrame


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
    </tr>
</table>
[7 rows x 4 columns]<br/>
</div>




```python
sf['Full Name'] = sf['First Name'] + ' ' + sf['Last Name']
```


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>




```python
sf['age'] * sf['age']
```




    dtype: int
    Rows: 7
    [576, 529, 484, 529, 529, 484, 625]



# Use the apply function to do a advance transformation of our data


```python
sf['Country']
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'USA', 'Poland', 'United States', 'Switzerland']




```python
sf['Country'].show()
```


<pre>Materializing SArray</pre>



<html>                 <body>                     <iframe style="border:0;margin:0" width="920" height="770" srcdoc='<html lang="en">                         <head>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega/5.4.0/vega.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-embed/4.0.0/vega-embed.js"></script>                             <script src="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.js"></script>                             <link rel="stylesheet" type="text/css" href="https://cdnjs.cloudflare.com/ajax/libs/vega-tooltip/0.5.1/vega-tooltip.min.css">                             <style>                             .vega-actions > a{                                 color:white;                                 text-decoration: none;                                 font-family: "Arial";                                 cursor:pointer;                                 padding:5px;                                 background:#AAAAAA;                                 border-radius:4px;                                 padding-left:10px;                                 padding-right:10px;                                 margin-right:5px;                             }                             .vega-actions{                                 margin-top:20px;                                 text-align:center                             }                            .vega-actions > a{                                 background:#999999;                            }                             </style>                         </head>                         <body>                             <div id="vis">                             </div>                             <script>                                 var vega_json = "{\"$schema\": \"https://vega.github.io/schema/vega/v4.json\", \"autosize\": {\"type\": \"fit\", \"resize\": false, \"contains\": \"padding\"}, \"padding\": 8, \"metadata\": {\"bubbleOpts\": {\"showAllFields\": false, \"fields\": [{\"field\": \"count\"}, {\"field\": \"label\"}, {\"field\": \"percentage\"}]}}, \"width\": 720, \"height\": 550, \"title\": \"Distribution of Values [string]\", \"style\": \"cell\", \"data\": [{\"name\": \"pts_store_store\"}, {\"name\": \"source_2\", \"values\": [{\"label\": \"United States\", \"label_idx\": 0, \"count\": 2, \"percentage\": \"28.5714%\"}, {\"label\": \"Canada\", \"label_idx\": 1, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"England\", \"label_idx\": 2, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Poland\", \"label_idx\": 3, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"Switzerland\", \"label_idx\": 4, \"count\": 1, \"percentage\": \"14.2857%\"}, {\"label\": \"USA\", \"label_idx\": 5, \"count\": 1, \"percentage\": \"14.2857%\"}]}, {\"name\": \"data_0\", \"source\": \"source_2\", \"transform\": [{\"type\": \"formula\", \"expr\": \"toNumber(datum[\\\"count\\\"])\", \"as\": \"count\"}, {\"type\": \"filter\", \"expr\": \"datum[\\\"count\\\"] !== null &amp;&amp; !isNaN(datum[\\\"count\\\"])\"}]}], \"signals\": [{\"name\": \"unit\", \"value\": {}, \"on\": [{\"events\": \"mousemove\", \"update\": \"isTuple(group()) ? group() : unit\"}]}, {\"name\": \"pts_store\", \"update\": \"data(\\\"pts_store_store\\\").length &amp;&amp; {count: data(\\\"pts_store_store\\\")[0].values[0]}\"}, {\"name\": \"pts_store_tuple\", \"value\": {}, \"on\": [{\"events\": [{\"source\": \"scope\", \"type\": \"click\"}], \"update\": \"datum &amp;&amp; item().mark.marktype !== &apos;group&apos; ? {unit: \\\"\\\", encodings: [\\\"x\\\"], fields: [\\\"count\\\"], values: [datum[\\\"count\\\"]]} : null\", \"force\": true}]}, {\"name\": \"pts_store_modify\", \"on\": [{\"events\": {\"signal\": \"pts_store_tuple\"}, \"update\": \"modify(\\\"pts_store_store\\\", pts_store_tuple, true)\"}]}], \"marks\": [{\"name\": \"marks\", \"type\": \"rect\", \"style\": [\"bar\"], \"from\": {\"data\": \"data_0\"}, \"encode\": {\"hover\": {\"fill\": {\"value\": \"#7EC2F3\"}}, \"update\": {\"x\": {\"scale\": \"x\", \"field\": \"count\"}, \"x2\": {\"scale\": \"x\", \"value\": 0}, \"y\": {\"scale\": \"y\", \"field\": \"label\"}, \"height\": {\"scale\": \"y\", \"band\": true}, \"fill\": {\"value\": \"#108EE9\"}}}}], \"scales\": [{\"name\": \"x\", \"type\": \"linear\", \"domain\": {\"data\": \"data_0\", \"field\": \"count\"}, \"range\": [0, {\"signal\": \"width\"}], \"nice\": true, \"zero\": true}, {\"name\": \"y\", \"type\": \"band\", \"domain\": {\"data\": \"data_0\", \"field\": \"label\", \"sort\": {\"op\": \"mean\", \"field\": \"label_idx\", \"order\": \"descending\"}}, \"range\": [{\"signal\": \"height\"}, 0], \"paddingInner\": 0.1, \"paddingOuter\": 0.05}], \"axes\": [{\"orient\": \"top\", \"scale\": \"x\", \"labelOverlap\": true, \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"title\": \"Count\", \"zindex\": 1}, {\"orient\": \"top\", \"scale\": \"x\", \"domain\": false, \"grid\": true, \"labels\": false, \"maxExtent\": 0, \"minExtent\": 0, \"tickCount\": {\"signal\": \"ceil(width/40)\"}, \"ticks\": false, \"zindex\": 0, \"gridScale\": \"y\"}, {\"scale\": \"y\", \"labelOverlap\": true, \"orient\": \"left\", \"title\": \"Values\", \"zindex\": 1}], \"config\": {\"axis\": {\"gridColor\": \"rgba(204,204,204,1.0)\", \"labelFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"labelFontSize\": 12, \"labelPadding\": 10, \"labelColor\": \"rgba(0,0,0,0.847)\", \"tickColor\": \"rgb(136,136,136)\", \"titleFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"titleFontWeight\": \"normal\", \"titlePadding\": 20, \"titleFontSize\": 14, \"titleColor\": \"rgba(0,0,0,0.847)\"}, \"axisY\": {\"minExtent\": 30}, \"legend\": {\"labelFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"labelColor\": \"rgba(0,0,0,0.847)\", \"titleFont\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"cornerRadius\": 30, \"gradientLength\": 608, \"titleColor\": \"rgba(0,0,0,0.847)\"}, \"range\": {\"heatmap\": {\"scheme\": \"greenblue\"}}, \"style\": {\"rect\": {\"stroke\": \"rgba(200, 200, 200, 0.5)\"}, \"cell\": {\"stroke\": \"transparent\"}, \"group-title\": {\"fontSize\": 29, \"font\": \"HelveticaNeue, Arial\", \"fontWeight\": \"normal\", \"fill\": \"rgba(0,0,0,0.65)\"}}, \"title\": {\"color\": \"rgba(0,0,0,0.847)\", \"font\": \"\\\"San Francisco\\\", HelveticaNeue, Arial\", \"fontSize\": 18, \"fontWeight\": \"normal\", \"offset\": 30}}}";                                 var vega_json_parsed = JSON.parse(vega_json);                                 var toolTipOpts = {                                     showAllFields: true                                 };                                 if(vega_json_parsed["metadata"] != null){                                     if(vega_json_parsed["metadata"]["bubbleOpts"] != null){                                         toolTipOpts = vega_json_parsed["metadata"]["bubbleOpts"];                                     };                                 };                                 vegaEmbed("#vis", vega_json_parsed).then(function (result) {                                     vegaTooltip.vega(result.view, toolTipOpts);                                  });                             </script>                         </body>                     </html>' src="demo_iframe_srcdoc.htm">                         <p>Your browser does not support iframes.</p>                     </iframe>                 </body>             </html>



```python
def transform_country(country):
    if country == 'USA':
        return 'United States'
    else:
        return country
```


```python
transform_country('Brazil')
```




    'Brazil'




```python
transform_country('Brasil')
```




    'Brasil'




```python
transform_country('USA')
```




    'United States'




```python
sf['Country']
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'USA', 'Poland', 'United States', 'Switzerland']




```python
sf['Country'].apply(transform_country)
```




    dtype: str
    Rows: 7
    ['United States', 'Canada', 'England', 'United States', 'Poland', 'United States', 'Switzerland']




```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">USA</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>




```python
sf['Country'] = sf['Country'].apply(transform_country)
```


```python
sf
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">First Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Last Name</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Country</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">age</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">Full Name</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Smith</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">24</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Bob Smith</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Williams</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Canada</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alice Williams</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Jone</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">England</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Malcolm Jone</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Brown</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Felix Brown</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Cooper</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Poland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">23</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Alex Cooper</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Campbell</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">United States</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">22</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Tod Campbell</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Ward</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Switzerland</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">25</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">Derek Ward</td>
    </tr>
</table>
[7 rows x 5 columns]<br/>
</div>


