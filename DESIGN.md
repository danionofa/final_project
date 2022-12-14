# Database Design

The SQLAlchemy database used in this design consists of two tables: users and hobbies, corresponding to the User and Hobby types, respectively.

Each User entry has the columns id, username, and password which corresponds to the registration form filled out when first interacting with Hobby Hollow. All passwords in this table are stored with a hash for user security. Additionally, the id column is set as a primary key in order for efficient querying and relation with the Hobby table.

Each Hobby entry has the columns id, name, overview, img, hobby_id, genres, user_id. The id is set as a primary key for the same reason as above. The name, overview, hobby_id, and genres columns store information about the hobby as retrieved from the API. The name column stores the title of the hobby, the overview column gives a short description of the hobby, the hobby_id gives the id of the hobby as stored in the API, and the genres column returns a string type list of genre ids, also retrieved from the API. The img column stores the path of the image as retrieved from the API.

# Front End
The front end of Hobby Hollow was implemented with Jinja for loops and if statements. The for loops were used to display the hobbies on screen while the if statements were used to ensure that the information displayed on the screen was relevant to the user that was currently logged in.

# Back End

## API Usage

I decided to use an API to populate data for Hobby Hollow instead of a set database, because I believed doing so would allow more flexibility in the movies and shows that users could possibly upload. [The Movie Database] (https://www.themoviedb.org/?language=en-US) provided a free API key for usage that I took advantage of for this project.

The first usage of the API was to look up information about the hobby that a user uploaded. The url in this case took in the name of the hobby as a search query as well as the type of hobby the user was searching for. The response generated varied depending on the type of hobby, so I used a nested try and except to return the proper data.

The second usage of the API was to show all movies/shows that had exactly the same set of genres as the hobbies that the user had already uploaded. The url in this case took in the type of hobby as well as the genres associated with that hobby. The response generated by this url also varied, so I used a nested try and except for returning data as well.

## Routing

I used "GET" requests when fetching a page, and "POST" requests when forms were submitted. I also called information from the API when necessary using the functions coded in the 'helpers.py' file. When interacting with the database I executed .query(), .execute(), and .commit() when necessary.