# python_api_challenge
WeatherPy File:

This assignment is creating a python script to display the weather of over 500 cities of varying distances from the equator.

Sections of Code:

1.Generate the Cities List by Using citipy Library:

This section is generating a cities list and displaying the number of cities in the list.

2.Use the OpenWeatherMap API to retrieve weather data from the cities list generated in the started code:

This section is using the OpenWeatherMap API to grab the cities and append them to a city data list.

This section is also converting the cities weather into a pandas dataframe and displaying the data.

3.Create the Scatter Plots Requested:

This section is fetching data from the city data dataframe and displaying the relationship between Latitude and it's other values(Max Temp, Humidity, Cloudiness, and Wind Speed) on scatter plots.

4. Computer Linear Regression for Each Relationship:

This section is defining a function to be able to call on later to create linear regression plots.

This section is also creating dataframes from the data in relation to the northern hemisphere and southern hemisphere.

This section plots relationships for both hemispheres(Max Temp Vs. Latitude, Humidity Vs. Latitude, Cloudiness Vs. Latitude, Wind Speed Vs. Latitude)

VacationPy File:

This file is creating python script to display hotels that are within a 10,000 metre radius of certian cities from a list.

Sections of Code:

1.Create a map that displays a point for every city in the `city_data_df` DataFrame. The size of the point should be the humidity in each city.

This sections generates a point for every city in the city data dataframe on a map where the size of each point is the humidity.

2. Narrow down the city data dataframe to find your ideal weather condition:

This section takes set values that fit a given criteria and turns the data into a filtered dataframe.

3. Create a new dataframe called hotel_df.

This section takes the last filtered dataframe and converts it into a new datframe to store the hotel names in.

4. For each city, use the Geoapify API to find the first hotel located within 10,000 metres

This section sets parameters to search for a hotel and iterates through the hotel_df to store the name in the dataframe. This also displays the data in a dataframe.

5. Add the hotel name and the country as additional information in the hover message for each city in the map.

This section generates a map plot and displays the data from the hotel_df dataframe and adds the hotel name and country as additional info.

I got/referenced the following code from Xpert Learning Assistant/GitHub

plt.scatter(city_data_df["Lat"], city_data_df["Max Temp"], marker="o", edgecolors="black", linewidths=1.5)

def linear_regress_plot(x, y, x_label, y_label, hemisphere, line_placement):

fig1, ax1 = plt.subplots(figsize=(10,8))

plt.annotate(linear_regress_eq, line_placement, fontsize=22, color='red')

plot_map = city_data_df.hvplot.points("Lng", "Lat", geo = True, tiles = "OSM", size = "Humidity", frame_width = 800, frame_height = 600, scale = 0.8, color = "City")

filtered_city_data_df = city_data_df.loc[(city_data_df['Max Temp'] < max_temp) &
                                     (city_data_df['Max Temp'] > min_temp) &
                                     (city_data_df['Wind Speed'] < max_wind_speed) &
                                     (city_data_df['Cloudiness'] <= max_cloudiness)
                                     ]

hotel_plot_map = hotel_df.hvplot.points("Lng", "Lat", geo = True, tiles = "OSM", frame_width = 800, frame_height = 600, scale = 0.8, color="City", hover_cols=['City', 'Hotel Name', 'Country'])
