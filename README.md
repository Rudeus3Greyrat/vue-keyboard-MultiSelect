# vue-keyboard-multiselect

>  A project for building a keyboard-supported MultiSelect component based on Vue.js.

## Build Setup

``` bash
# install dependencies
npm i vue-keyboard-multiselect
See https://www.npmjs.com/package/vue-keyboard-multiselect for more information.
```

## How to Use

``` bash
Include your list of elements rendered by your data in <KeyboardMultiSelect></KeyboardMultiSelect>.
Then you can multi-select these elements using keyboard shortcut.
Hold 'Command' for multi-select one by one. Hold 'Command' with 'Shift' for multi-select a section in your list of elements.
```

## Props

``` bash
Name: rawData
Type: Array
Default: []
Description: An array of data source that is used ro render your html fragment in <KeyboardMultiSelect></KeyboardMultiSelect>.
```

## Events

``` bash
Name: selectChange
Description: Emitted whenever select of your data is changed. Param is changed selected data array of your raw data.
Params:listData
```
For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).

