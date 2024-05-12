## Wellness Exercises DB

This is a repository that contains all the exercises that are used in the wellness app. The exercises are stored as `JSON` files and are bundled into a single `JSON` file that is used in the app. The images for the exercises are stored in the repository and are fetched from the `GitHub` raw content URL.

### Schema

All exercises are stored as seperate `JSON` documents and conform to the following [JSON Schema](./schema.json) eg.

```json
{
  "id": "Alternate_Incline_Dumbbell_Curl",
  "name": "Alternate Incline Dumbbell Curl",
  "force": "pull",
  "level": "beginner",
  "mechanic": "isolation",
  "equipment": "dumbbell",
  "primaryMuscles": [
    "biceps"
  ],
  "secondaryMuscles": [
    "forearms"
  ],
  "instructions": [
    "Sit down on an incline bench with a dumbbell in each hand being held at arms length. Tip: Keep the elbows close to the torso.This will be your starting position.",
  ],
  "category": "strength",
  "images": [
    "Alternate_Incline_Dumbbell_Curl/0.jpg",
    "Alternate_Incline_Dumbbell_Curl/1.jpg"
  ]
}
```
See [Alternate_Incline_Dumbbell_Curl.json](./exercises/Alternate_Incline_Dumbbell_Curl.json)

### How we use them?

A copy of all the exercises when combining all the `JSON` files into a single `JSON` file can be found [here](./dist/exercises.json), this file that is created is bundled with the app and is used to display the exercises to the user. The images in the other hand are only stored in this repository and are fetched from the `GitHub` repository when needed using the `GitHub raw content` URL.

### Add, Edit or Remove exercises

To add, edit or remove exercises you can do so by creating a new `JSON` file in the [exercises](./exercises) directory. The file should contain the exercise details and should conform to the [schema.json](./schema.json) schema. Also add the corresponding images, after this, run the make task to combine all the `JSON` files into a single file and commit the changes. Then copy the new `JSON` file into the wellness app.

### Build tasks
There are a number of helpful [Makefile](./Makefile) tasks that you can utilize

#### Linting
To lint all the `JSON` files against the [schema.json](./schema.json) use

```
make lint
```

#### Combining into a single JSON file
If you make changes to any of the exercises or add new ones, to recombine all single `JSON` files into a single `JSON` containing an array of objects using the following make task

```sh
make dist/exercises.json
```
_Note: requires [jq](https://stedolan.github.io/jq/)_

