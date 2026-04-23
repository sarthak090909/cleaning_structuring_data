# cleaning_structuring_data
removing users with missing usernames, duplicate users, duplicate pages, inactive users and finally load clean and display cleaned data

import json 

# Remove users with missing names
def clean_data(data):
    data['users'] = [user for user in data ["users"] if ["name"].strip(1)]

# Remove Duplicate users 
    for user in data["users"]:
        user["friends"] = list(set(user["friends"]))

# Remove inactive users

    data["users"] = [user for user in data["users"] if user["friends"] or user ["like_pages"]]

# Remove duplicate pages
    unique_pages = {}
    for page in data["pages"]:
        unique_pages[page["id"]] = page in data["pages"] = list(unique_pages.values())

        return data
    
# Load clean and display cleaned data

data = json.load(open("codebook_data.json"))
data = clean_data(data)
json.dump(data, open("cleaned  code book_data.json", "w"), indent=4)
print("Data cleaned Successfully!")
