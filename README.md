Download Link: https://assignmentchef.com/product/solved-csci1100-homework-9-dictionaries-and-classes
<br>
Part 1: Yelp Business CategoriesYou are given the actual Yelp database from Lab 5 in JSON form in a file called businesses.json.Each line of the file is a json formatted string corresponding to a business. For example, thefollowing program will read any print the business information from the first line of the file:import jsonf = open(‘businesses.json’)line = f.readline()business = json.loads(line)print business[‘name’]print business[‘categories’]will result in the following output:Mustang BBQ[u’Food’, u’Specialty Food’, u’Meat Shops’, u’Barbeque’, u’Restaurants’]Associated with each business is a list of categories given by the Yelp users. Recall that JSON willreturn Unicode strings (e.g. u’Food’ above) which you can treat like regular strings.Write a program that reads a category name (correctly spelled) and a cutoff value (a valid integer).Your program must count all categories that co-occur with the given category and print thosecategories with counts greater than the given cutoff in sorted order. Right align the category namesto 30 characters. For example, after processing the above business, we will find that categories‘Food’,’Specialty Food’,’Meat Shops’,’Barbeque’ each occur at least once. You will upEnter a category == RestaurantsRestaurantsCutoff for displaying categories = 44Categories co-occurring with Restaurants:American (Traditional): 4Breakfast &amp; Brunch: 4Chinese: 6Delis: 4Food: 8Pizza: 17Sandwiches: 4Seafood: 4Note: Interestingly, not all Restaurants are considered Food and more restaurants are consideredPizza than Food! Here is one more example.Enter a category == ShoppingShoppingCutoff for displaying categories = 22Categories co-occurring with Shopping:Books, Mags, Music and Video: 3Comic Books: 2Home &amp; Garden: 2Jewelry: 2If the searched category is not found, your program must print Searched category is not found.If there are no categories to print (none co-occurring or are above cutoff), your program must printNone above the cutoff. See example runs below.Enter a category == restaurantsrestaurantsCutoff for displaying categories = 44Searched category is not foundEnter a category == ShoppingShoppingCutoff for displaying categories = 55Categories co-occurring with Shopping:None above the cutoffPart 2: Yelp Business Reviews (optional/bonus part)In this part, we will use two files. The first one is the file called businesses.json describedin part 1. Note that each business is associated with a ‘business_id’ that uniquely identifiesthat business. Two businesses may have the same name, corresponding to the different stores indifferent locations. These will have different ‘business_id’ values. For example, in the file givento you, you have two different stores for “Hannaford Supermarkets” with ‘business_id’ values:‘UZFBK4pU-VcEt1N4IoYCRA’ and ‘LO0TfAyhOYR8fVuido_9aA’.In addition to this, you are given a second file called reviews.json. This file contains one reviewfor a business in each line. You are only interested in the review text and the ‘business_id’ foreach review. For example, the following program will read any print the review for the first line ofthe file:import jsonf = open(‘reviews.json’)line = f.readline()review = json.loads(line)print review[‘business_id’]printprint review[‘text’]will result in the following output (formatting added by me):gekPL0Kc7w9zLDT3EulvxQGreat fish fry. The fish is fresh and comes in a great portion size.Service is good. Having left the area, I really miss this place.Write a program that reads the name of a business using raw_input and finds the reviews for allthe stores of the given business. Your program must print the reviews in order they are found inthe file, formatted with four spaces on the left and broken into lines using textwrap. Note: If thereare new lines in the review, you must preserve those (textwrap will remove them). If the searchedbusiness is not found, print a message. If no review is found for the given business, print a message.Example runs are given below.Enter a business name = Bombers Burrito BarBombers Burrito BarThis business is not foundEnter a business name = Rensselaer Polytechnic InstituteRensselaer Polytechnic InstituteNo reviews for this business is foundEnter a business name = Country True Value HardwareCountry True Value HardwareReview 1:Best customer service, and they have everything.Review 2:This is my one stop shop for most of my basic hardware and home andgarden needs because I’m in and out of here in no time. There’s enoughparking around the building, which is close to the front door. CountryTrue Value is not the cheapest pricewise, but most items areconvenient for me to find. The employees are easy to track down andare very helpful in locating items in the store when I need them.Earlier this month, I ended up buying my grass seed here instead of atHome Depot because I couldn’t wait around for the Home Depot employeeto use the forklift while it was pouring rain outside. Of course, Ipaid a little more here for the convenience.Sometimes smaller is better!Finally, note that the business below has multiple stores:Enter a business name = Ted’s Fish FryTed’s Fish FryReview 1:Great fish fry. The fish is fresh and comes in a great portion size.Service is good. Having left the area, I really miss this place.Review 2:Best fish fries in the Albany area.Review 3:Ted’s Fish Fry now has an official website and a Facebook page!Congrats on almost 60 years in business!They have some very cool photos on both, hehe :-OWEBSITE: http://www.tedsfishfry.netFACEBOOK: http://www.facebook.com/pages/Watervliet-NY/Teds-FishFry/240983270362Review 4:3 stars is just about right. The fish frys are very good, although Ididn’t like their chili sauce…it was more like relish, but therewere a lot of regular customers ordering it so ymmv. Had a fish frywith cocktail sauce and tartar that was very good. The staff here justyell the food back to the kitchen help and they are always getting itscrewed up or miscommunicated…comical, maybe that is part of thecharm? I also had a hot dog and the sauce is sort of bland…I preferhot dog sauce with a lot more flavor and kick. They also had carrotcake and cheesecake available…figured they had to be great…thecarrot cake was a little dry. Go eat fish frys, figure out what youlike on them and you will be good to go.Part 3: Battleship Game (optional/bonus part)In this part, you will implement a simple game of battleship. The list of all battleships (or shipsas we will call them) and all player moves are given in a single file. Your program must read thename of the file using raw_input.The first line of the file tells you how many ships there are, followed by the description of eachship. Then, all the player moves are given. Read the ships first, then perform all player movesuntil either no more moves left or a player wins.Your program must define and use a class called Battleship that stores relevant information abouteach ship. Define the class in the same file as your homework description to simplify submission.Each ship has the following information:Name|x|y|length|height|healthEach ship is a rectangle with upper left corner at x,y and lower right corner at x+length, y+height.The health defines how many hits it takes to sink this ship. Best news: ships don’t move. Evenbetter news: all players take aim at the same set of ships for simplicity.Each player move is given by:Player Name|x|ywhich means that a player with the given name has fired a torpedo at the coordinates (x,y). Youcan assume players are taking turns and the input is valid. Each time a player hits a ship, displaya message. If the player hits completely, display a message as well. Anyime the ship is hit, itshealth is decremented by one. Whenever the health reaches zero, the ship has sunk. We displaya message. A player cannot hit a sunken ship. When printing ship names, right justify them 12characters.Anytime a player sinks a ship and there are no ships left, the game ends immediately and displaythat the current player has won. If all the moves are played and there are still some ships left, yourprogram must print No player won!.We have provided two sample inputs and outputs in the ZIP file for this homework.Submission InstructionsPlease note that the files we use on the submission server are likely going to be different than theones we have given you.Please follow these instructions carefully.Part 1. Submit a single file called hw9 part1.py that assumes the existence of a file calledbusinesses.json. Your program must read a single category and an integer cutoff value usingraw_input and return all the matching categories in sorted order.Part 2. Submit a single file called hw9 part2.py that assumes the existence of two files calledbusinesses.json and reviews.json. Your program must read the name of a restaurant usingraw_input and return all the matching reviews in the order they are found in the file.Part 3. Submit a single file called hw9 part3.py that reads the name of a file using raw_inputcontaining the number of ships, the information for each ship on a single line and then all the playermoves. Items on a line are separated by |