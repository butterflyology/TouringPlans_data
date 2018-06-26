### TouringPlans data

After reading the TouringPlans [blog post](https://blog.touringplans.com/2018/06/25/disney-world-wait-times-available-for-data-science-and-machine-learning/) I thought it would be a good idea to create a github repo containing the [data sets](https://touringplans.com/walt-disney-world/crowd-calendar#DataSets). Since these are relational data I've gone ahead and made an `SQLite` database to help manage the data.


---

The files and directories in this repository are:

-   <kbd>data/</kdb>
  - `dinosaur.csv` - DINOSAUR (Disney's Animal Kingdom)
  - `expedition_everest.csv` - Expedition Everest (Disney's Animal Kingdom) -  observations
  - `kilimanjaro_safaris.csv` - Kilimanjaro Safaris (Disney's Animal Kingdom)
  - `metadata.csv` - Metadata common to all datasets
  - `pirates_of_caribbean.csv` - Pirates of the Caribbean (Magic Kingdom)
  - `rock_n_rollercoaster.csv` Rock 'n' Roller Coaster (Disney's Hollywood Studios)
  - `soarin.csv` - Soarin' (Epcot)
  - `spaceship_earth.csv` - Spaceship Earth (Epcot)
  - `splash_mountain.csv` - Splash Mountain (Magic Kingdom)
  - `toy_story_mania.csv` - Toy Story Mania! (Disney's Hollywood Studios)

- `README.md` - This file.
- `touringplans_data_dictionary.xlsx` -  The file that contains the explanations for the variables in the datasets. This spreadsheet has 5 tabs.

---


A nice `INNER JOIN` will allow you to link the metadata with the wait times, thus creating the appropriate dataset. For example:

`SELECT * FROM dinosaur INNER JOIN  metadata ON dinosaur.date = metadata.DATE`

This query returns an object with 185562 observations and 193 variables. *nb* that there are now two columns (`date` and `DATE`) that contain the same information. `SQLite` does not support removing columns so remember to deal with those (and the `datetime` column) when you are preparing your data for analysis.

I have saved all of the data `JOIN`s as `VIEW`s within the database. Each `JOIN` is saved with the name `_VIEW` appended to the name of the dataset. For example, the `JOIN` for `dinosaur` and `metadata` is saved as `dinosaur_VIEW`.


---

Here are the `shasum` / `md5` values and the number of observations to ensure the  integrity of the data files:


| File  | `shasum` | `md5` | Observations |
|:-:|:-:|:-:|:-:|
| `dinosaur.csv` | bfa3e121eac34751229611910652a9256894e1fb  |   c6fd9a43f9d8e89c6092532e8f7b0bcc | 185562 |
| `expedition_everest.csv`  | cd6f131611e9f33dce9caa4ada2f2bbb0ed7984e | 1df1b1399c8fa69f0f78421f638e116b | 204697 |
| `kilimanjaro_safaris.csv` | f28d3412779e088485e8a59c3659f439deb8121a | 4b482465e9474b2af3945ba8b32e3db7 | 193310 |
| `metadata.csv` | 39e65f286b9215879dc41cca8a627a539e38858c | 4875ae9455a76c4611c13fecd88b9945 | 2358 |
| `pirates_of_caribbean.csv` | 6577bd3961e7227effe31dafd873169fb892ce65 | 8e6461d44ff9c1d3170ed3a5d7393e9f | 237486 |
| `rock_n_rollercoaster.csv` | 8e63e74d511f75333ccb6aefd41aea54748afa8a | b7e983298384baf68f98ed3750752c02 | 225596 |
| `soarin.csv` | d693ddb56d3584286b257399eb7c6b53cf36a1a5 | 2a5994c04b389739352fa3a9ed25ccc4 | 225633 |
| `spaceship_earth.csv` | 65948e2265722bbfc12641c8e9228c4ac70fa2b5 | 9ae1a41917b0c70e060e263fd537ed9b | 226426 |
| `splash_mountain.csv` | 8cd8860421a8d2482334c9cbffb4caa58aeaad22 | 87d21d83b2de05fa1f27fcc3bbce327b | 221824 |
| `toy_story_mania.csv` | 7efbe8dfeb055d17cbb90f158a05811d852034b4 | 0f1ae7a9b1de60e7d258733fc0eccbd7 | 227221 |

Here are the `shasum` / `md5` values for the `sqlite` database:

| File  | `shasum` | `md5` |
|:-:|:-:|:-:|
| `TouringPlans.db` | 7be9bc2ff27aa56908d10d1a42c78321750b061d | fc9c7ad755991a5ebf0cfc496b8d2437 |


---

If you find any problems with the repository or data integrity, please let me know and open an [issue](https://github.com/butterflyology/TouringPlans_data/issues). 
