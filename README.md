<img src="/gitImages/TheOfficeEpisodeGeneratorLogo.png" alt="The Office Episode Generator Logo">

A Python-based program that generates a random episode from The Office (U.S).

# Requirements and Dependencies

This program makes use of the following packages:

- [Cinemagoer](https://github.com/cinemagoer/cinemagoer) (formerly known as *IMDbPY*)
- [Python Imaging Library](https://github.com/python-pillow/Pillow)
- [Pyfiglet](https://github.com/pwaller/pyfiglet)

```pip install cinemagoer
python3 -m pip install cinemagoer
```

```
python3 -m pip install Pillow
```

```
python3 -m pip install pyfiglet
```

# Methodology

An instance from the Cinemagoer class is created. The `movieID` for *The Office (U.S)* is then used to load all the episodes of the series from IMDb. All the episodes are placed into a text file. Furthermore, after that text file is created, that text file will be used to display a random line which in this case displays the episode in said line.

```python
def loadEpList():
    imdb_instance = imdb.IMDb()
    imdb_code = "0386676"

    series = imdb_instance.get_movie(imdb_code)
    imdb_instance.update(series, 'episodes')
    episodes = series.data['episodes']
    with open("episode_list.txt", "w") as f:
        for i in episodes.keys():
            for j in episodes[i]:
                title = episodes[i][j]['title']
                if j < 10:
                    ep_num = "E0" + str(j)
                else:
                    ep_num = "E" + str(j)
                f.write("S0" + str(i) + ep_num + " : " + title + "\n")
```

<img src="/gitImages/loadingDisplaying.gif" alt="Program Functioning">
