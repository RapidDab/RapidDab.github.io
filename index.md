# Hello World

This is my home page! My name is Your Name and I am a student at [Cal State Fullerton](http://www.fullerton.edu/) and my major is Computer Science.

## Computer Science Projects

My GitHub page is http://github.com/RapidDab.

### CPSC 120

* Lab 6

    Lab 6, part 2 was one of my favorite labs because of how I made use of ||(or) and &&(and) statements. Another way I could have done the conditional statements in the functions that check which type of card the user inputed is to write seperate if and else if statements for each conditional. I think the way I did was better and a lot more fun to do instead of hard coding each statement. Also something I found interest in this lab was that I had to use a try, throw catch statement in the IsNumberCard function because i needed to account for the card being inputed as a string and a integer. Instead of checking if the user inputed an integer or a string I just used a try, throw, catch statement to ignore if the card_name was an string with actual letters.

    **The Code**
    ```c++
    bool IsAce(const std::string& card_name) {
        if (card_name == "A") {
            return true;
        } else {
            return false;
        }
    }

    bool IsFaceCard(const std::string& card_name) {
        if (card_name == "J" || card_name == "Q" || card_name == "K") {
            return true;
        } else {
            return false;
        }
    }

    bool IsNumberCard(const std::string& card_name) {
    try {
        std::string copy_card_name{card_name};
        int int_to_string{std::stoi(copy_card_name)};
        if (int_to_string >= 2 && int_to_string <= 10) {
            return true;
        } else {
            throw false;
        }
    } catch (...) {
        return false;
    }
    }

    bool IsCardName(const std::string& str) {
        if (IsAce(str) || IsFaceCard(str) || IsNumberCard(str)) {
            return true;
        } else {
            return false;
        }
    }
    ```


* Lab 7

    Lab 7, part 2 was one of my favorite labs because to debug the code and complete the lab I had to impliment function overloading to validate if the user_input was valid for the street, day, and hour. The street and day are both strings but hour is an integer. I used function overloading to see if the user inputed valide values. One function with parameters for strings and another for integers. 


    **The Function**
    ```c++
    /*Parameters: (the vector you are searching from, argument you are saying is valide or not, 
                    the element you are trying to find)*/
    bool ValidateArgument(const std::vector<std::string> &names_list,
                      std::string argument_element, std::string find_element) {
    if (std::find(names_list.begin(), names_list.end(), find_element) ==
        names_list.end()) {
        std::cout << "error: invalid " << argument_element;
        return false;
    }
    return true;
    }
    bool ValidateArgument(const std::vector<int> &names_list,
                        std::string argument_element, int find_element) {
    if (std::find(names_list.begin(), names_list.end(), find_element) ==
        names_list.end()) {
        std::cout << "error: invalid " << argument_element;
        return false;
    }
    return true;
    }
    ```

    **The implication**
    ```c++
    std::string street{arguments[1]};
    std::string day{arguments[2]};

    int hour{std::stoi(arguments[3])};

    int minute{std::stoi(arguments[4])};

    //Checking if the user input is inside the vector of valide street names
    std::vector<std::string> street_names{"ash", "beech", "cedar", "date", "elm"};
    if (ValidateArgument(street_names, "street", street) == false) {
        return -1;
    }
    //Checking if the user input is inside the vector of valide day names
    std::vector<std::string> day_names{"mon", "tue", "wed", "thu",
                                        "fri", "sat", "sun"};
    if (ValidateArgument(day_names, "day", day) == false) {
        return -1;
    }
    //Checking if the user input is inside the vector of valide hours
    std::vector<int> hour_num(24);
    std::iota(hour_num.begin(), hour_num.end(), 1);
    if (ValidateArgument(hour_num, "hour", hour) == false) {
        return -1;
    }
    //Checking if the user input is inside the vector of valide minutes
    std::vector<int> minu_num(59);
    std::iota(minu_num.begin(), minu_num.end(), 0);
    if (ValidateArgument(minu_num, "minute", minute) == false) {
        return -1;
    }

    ```
* Lab 10
    
    Lab 10 part-2 is another one of my favorite labs because its the first time I implemented nested for loops and 2-D vectors indexing. It helped me to think three dimentially and figure out how to loop through the inside(**ca_coutie**) and outside vectors(**ca_countie**). It was also interesting that I had to use the two different formats for for loops for the function.**CountryIndex**. 

    **The code**
    ```c++
    int CountyIndex(const std::vector<std::vector<std::string>>& ca_counties,
                const std::string& match_county) {
    int index{-1};
    //Loops through the outside vector(ca_couties)
    for (const auto& ca_countie : ca_counties) {
        //Loops through the vector inside the outside vector (ca_countie)
        for (int k = 0; k < ca_countie.size(); k++) {
            if (match_county == ca_countie[k]) {
                index = {k};
            }
        }
    }
    return index;
    }
    ```