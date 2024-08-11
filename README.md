# Sgraph Component

This Svelte component allows you to create customizable bar graphs with a fixed y-axis representing time and a flexible x-axis for any other data.

## Features

- **Fixed Y-Axis (Time):** The y-axis is pre-configured to display time.
- **Customizable X-Axis:** The x-axis can be configured to represent any type of data.


## Usage

Install the component:

`npm install sveltegraph`

Import the component:

`import { Sgraph } from 'sveltegraph'`

Use the component in your project:

```
<script>
    import { Sgraph } from 'sveltegraph';

    const items = [
        {'title': 'item1', 'time': 3*60},
        {'title': 'item2', 'time': 1*60},
        {'title': 'item3', 'time': 2*60}]
</script>

<Sgraph x-items={items}>
```

- x-items prop takes an array of objects that has a title and a time represented in seconds.


## License
This project is under the MIT License