![header](/images/autocomplete1.png)

!!! quote "From Google Material Design documentation."
    Use auto-complete text fields to present real-time suggestions or completions in dropdowns, so users can enter information more accurately and efficiently.


### How to add?

I. Declare your `AutoCompleteTextView` inside any `layout.xml`.

```xml
<AutoCompleteTextView
    android:id="@+id/autocompleteView"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Search dogs..."/>
```

II. Define a `string-array` that contains all text suggestions in a file inside `res/values` directory.

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string-array name="dogs_list">
        <item>Bichon Frise</item>
        <item>Border Collie</item>
        <item>Border Terrier</item>
        <item>Boxer</item>
        <item>Chihuahua</item>
        <item>German Shepherd</item>
        <item>Golden Retriever</item>
        <item>Greyhound</item>
    </string-array>
</resources>
```

III. Define a `filterable list adapter` to manage the auto completion data list.

```java
int layoutItemId = android.R.layout.simple_dropdown_item_1line;
String[] dogsArr = getResources().getStringArray(R.array.dogs_list);
List<String> dogList = Arrays.asList(dogsArr);
ArrayAdapter<String> adapter = new ArrayAdapter<>(this, layoutItemId, dogList);

AutoCompleteTextView autocompleteView =
    (AutoCompleteTextView) findViewById(R.id.autocompleteView);
autocompleteView.setAdapter(adapter);
```

### How to style?
![style](/images/autocomplete2.png)

I. Declare custom styles in your `styles.xml` file.

```xml
 <style name="Autocomplete" parent="Widget.AppCompat.Light.AutoCompleteTextView">
    <item name="android:background">@color/green500</item>
    <item name="colorControlNormal">@color/amber500</item>
    <item name="colorControlActivated">@color/cyan500</item>
</style>
```

II. Apply this style to the `AutoCompleteTextView ` via `android:theme` attribute.

```xml
<AutoCompleteTextView
    android:id="@+id/autocomplete_dogs"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:theme="@style/Autocomplete"
    android:hint="Search dogs..." />
```

### Drop down anchor
![style](/images/autocomplete3.png)

By default, the dropdown list with your filtered data appear just below the `AutoCompleteTextView`.

To change this position use `dropDownAnchor` attribute and reference another view id.

```xml
<AutoCompleteTextView
    android:id="@+id/autocomplete_dogs"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:theme="@style/Autocomplete"
    android:hint="Search dogs..."
    android:dropDownAnchor="@+id/header"
    android:dropDownWidth="match_parent"
    />
```

## Custom Adapter
![style](/images/autocomplete4.png)

To fully customize the dropdown list you need to provide your own `Adapter`. It needs to implement `Filterable` and `ListAdapter` interfaces.

The easiest way to achieve this is by extending `ArrayAdapter` which already implements both interfaces.


I. Create a custom adapter extending `ArrayAdapter` class.

```java
class AutoCompleteDogsAdapter extends ArrayAdapter<Dog> {
  ...
}
```

II. Create a custom filter extending `Filter` class and provide your own filtering logic overriding `performFiltering` method.

```java
class DogsFilter extends Filter {

    AutoCompleteDogsAdapter adapter;
    List<Dog> originalList;
    List<Dog> filteredList;

    public DogsFilter(AutoCompleteDogsAdapter adapter, List<Dog> originalList) {
        super();
        this.adapter = adapter;
        this.originalList = originalList;
        this.filteredList = new ArrayList<>();
    }

    @Override
    protected FilterResults performFiltering(CharSequence constraint) {
        filteredList.clear();
        final FilterResults results = new FilterResults();

        if (constraint == null || constraint.length() == 0) {
            filteredList.addAll(originalList);
        } else {
            final String filterPattern = constraint.toString().toLowerCase().trim();

			      // Your filtering logic goes in here
            for (final Dog dog : originalList) {
                if (dog.breed.toLowerCase().contains(filterPattern)) {
                    filteredList.add(dog);
                }
            }
        }
        results.values = filteredList;
        results.count = filteredList.size();
        return results;
    }

    @Override
    protected void publishResults(CharSequence constraint, FilterResults results) {
        adapter.filteredDogs.clear();
        adapter.filteredDogs.addAll((List) results.values);
        adapter.notifyDataSetChanged();
    }
}
```

III. Provide your custom filter from your adapter class by overriding `getFilter()` method.

```java
class AutoCompleteDogsAdapter extends ArrayAdapter<Dog> {

    private final List<Dog> dogs;
    private List<Dog> filteredDogs = new ArrayList<>();

    public AutoCompleteDogsAdapter(Context context, List<Dog> dogs) {
        super(context, 0, dogs);
        this.dogs = dogs;
    }

    @Override
    public int getCount() {
        return filteredDogs.size();
    }

    @Override
    public Filter getFilter() {
        return new DogsFilter(this, dogs);
    }

    @Override
    public View getView(int position, View convertView, ViewGroup parent) {
        // Get the data item from filtered list.
        Dog dog = filteredDogs.get(position);

	    // Inflate your custom row layout as usual.
        LayoutInflater inflater = LayoutInflater.from(getContext());
        convertView = inflater.inflate(R.layout.row_dog, parent, false);

        TextView tvName = (TextView) convertView.findViewById(R.id.row_breed);
        ImageView ivIcon = (ImageView) convertView.findViewById(R.id.row_icon);
        tvName.setText(dog.breed);
        ivIcon.setImageResource(dog.drawable);

        return convertView;
    }
```
