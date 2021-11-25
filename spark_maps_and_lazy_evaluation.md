
# Maps



```python
import pyspark
sc = pyspark.SparkContext(appName="maps_and_lazy_evaluation_example")

log_of_songs = [
        "Despacito",
        "Nice for what",
        "No tears left to cry",
        "Despacito",
        "Havana",
        "In my feelings",
        "Nice for what",
        "despacito",
        "All the stars"
]

# parallelize the log_of_songs to use with Spark
distributed_song_log = sc.parallelize(log_of_songs)
```


```python
def convert_song_to_lowercase(song):
    return song.lower()

convert_song_to_lowercase("Havana")
```




    'havana'




```python
distributed_song_log.map(convert_song_to_lowercase)
```




    PythonRDD[1] at RDD at PythonRDD.scala:53




```python
distributed_song_log.map(convert_song_to_lowercase).collect()
```




    ['despacito',
     'nice for what',
     'no tears left to cry',
     'despacito',
     'havana',
     'in my feelings',
     'nice for what',
     'despacito',
     'all the stars']




```python
distributed_song_log.collect()
```




    ['Despacito',
     'Nice for what',
     'No tears left to cry',
     'Despacito',
     'Havana',
     'In my feelings',
     'Nice for what',
     'despacito',
     'All the stars']




```python
distributed_song_log.map(lambda song: song.lower()).collect()
```




    ['despacito',
     'nice for what',
     'no tears left to cry',
     'despacito',
     'havana',
     'in my feelings',
     'nice for what',
     'despacito',
     'all the stars']


