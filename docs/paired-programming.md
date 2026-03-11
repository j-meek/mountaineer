
# Goal of the project: Is it clear to you from the proposal.md how the goal can be accomplished using Python and the specified packages?

Yes most definitely! Using both what we learned about REST APIs as well as pandas, the data necessary for the package can be accessed and organized in a neat manner. I am not very farmiliar with geopandas but from my initial read through of the documentation it looks to be very useful for visualization and helping present the data in the best way possible to the user.

# The Data: Is it clear to you from the proposal.md what the data for this project is, or will look like?

The data for this project is clear as it will be a filtered pandas dataframe which includes a species name/genus, latitude, and longitude. What is a bit unclear is how exactly the data will be presented visually through geopandas (what exactly will the graph look like or what colors and fonts will be used) however the frontend of an app can constantly be tweaked to be more user friendly.

# The code: (Look at the Python code files in detail first and try to comprehend a bit of what is written so far)

- Does the current code include a proper skeleton (pseudocode) for starting this project?

Yes, many of the functions are named clearly to express their purpose and progress in a logical manner such as first getting the occurences, then converting to a dataframe, then graphing. I would argue there is even more than a skeleton as there is already functioning and well written code for getting occurences.

- What can this code do so far?

As explained above, the code can already pull data from the gbif API returning a JSON result for a query. The next step will be to convert and organize this data in a pandas df, followed by presenting it visually in a nice manner.

- Given the project description, what are some individual functions that could be written to accomplish parts of this goal?

Potential names for functions that would still need to be written include: create_df() and visualize_df(). The current skeleton has these functions as convert_json_to_dataframe(self) and plot_with_mpl(self).

# Code contributions/ideas: See description below for what to write here.

Unfortunately, I could not read the file that I was supposed to read according to the original code which meant I could not test any of the code I wrote. I spent a long time just trying different ways to read it even manually inputting the complete full path but that did not work either for some reason. I messaged Jared about this but unfortunately did not hear back before the deadline so I will just turn in the code that I think is on the right track and should theoretically work or be close to working. 

My first contribution was the convert_json_df function which converts the output created from the get_occurences function Jared already wrote to a pandas df. From here the next step is to organize the df but because I could not run the code I could not visualize it to make sure it was being organized correctly. Because of this I wanted to include several ways that the df could be filtered so I wrote the next step in 2 different ways (by string or by column index) so there would be options. I also included a link to the stack overlflow post that helped me with this and has more information on organizing df's if Jared should choose to filter it differently. Next I looked to the plotting function and realized I would need to import matplotlib. After reading through and searching matplotlib and geopandas documentation I came across a post that I think could help do exactly what is necessary. I wrote code based off the post that I think should be close to working but again because I could not test it I am unsure if this works. The plot_with_mpl function converts the outputted df from the convert_json function to a geopandas geodataframe and plots it with matplotlib.
