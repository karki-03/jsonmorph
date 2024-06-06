# jsonmorph

jsonmorph is a tool for transforming a JSON to another JSON by defining a configuration JSON setting file.

## Use Cases:
1. <b>Data Transformation for API Responses</b>: Transforming user profile data from one format to another before sending it to a third-party analytics service.
2. <b>Configurable Data Migration</b>: Migrating customer data from an old CRM system to a new one, where the data fields and structures differ.
3. <b>Dynamic Data Generation for Testing</b>: Generating mock order data with current timestamps to test an order processing system.
4. <b>Enhancing Data Privacy</b>: Replacing user email addresses and phone numbers with fixed strings or null values before logging user activity data.


## Features

- In-built functions to customize the output JSON.
- Designed for seamlessly transforming JSON to another JSON.
- Simple and easy-to-use.

## Installation

You can install jsonmorph using pip:

```
pip install jsonmorph
```

## In-built functions

- To be used as a value in the settings json.

1. Fixed String: `{{string('sample_fixed_string')}}`
2. Current datetime: `{{now()}}`
3. NULL value: `{{NULL}}`

## Example Usage
```
from jsonmorph import process_json

try:
    output_json = process_json("your_fav_directory/input.json", "your_fav_directory/setting.json", "your_fav_directory/output.json")
    print(output_json)
except Exception as e:
    print(f"Error: {e}")
```

## Sample JSON files

1. input.json : Will contain the original JSON.
```
{
    "name": "Bidut Karki",
    "address": {
        "street" : "Developers paradise"
    }
}
```

2. setting.json : You will have to compose this, using the in build functions and path of the nested values.
```
{
    "myname" : "name",
    "age": "{{NULL}}",
    "street_add": "address.street",
    "planet":"{{string('Earth')}}",
    "datetime":"{{now()}}"
}
```
3. output.json : Will be generated automatically when process_json function is called.
```
{
    "myname": "Bidut Karki",
    "age": null,
    "street_add": "Developers paradise",
    "planet": "Earth",
    "datetime": "Tue Jun 04 2024 10:54:14 GMT-0000 (UTC)"
}
```

## Testing
- This is basically for testing the library if you clone it from github and try to add any feature. Otherwise, you don't need it to use the library.

```
python3 -m unittest jsonmorph/tests/test_main.py
```

## Contributing

Contributions are welcome! If you encounter any issues or have suggestions for improvements, please open an issue on the GitHub repository.
License

## Contact
- Email: bidutjava3@gmail.com
- Github: https://github.com/karki-03
- Website: bidutkarki.com
- LinkedIn: https://www.linkedin.com/in/bidutkarki/

In case, of any bug or any suggestion, do drop a mail or connect with me on linkedin.

#### `jsonmorph` is released under the MIT License. See the LICENSE file for more details. 
