# Introduction #

A progressive enhancement to `<select multiple>` form elements. It provides a simpler alternative with the following advantages:

  * Easier for users to understand and interact with than regular `<select multiple>` form elements. Users know how to interact with it sans instruction.

  * Doesn't require user to Ctrl-Click or Shift-Click multiple elements. Instead users of your form can add or remove elements individually, without risk of losing those that have already been selected.

  * Selected elements are always visible (within the confines of your interface) while unselected elements are always hidden (within a regular `<select>`).

  * Unlike regular `<select multiple>` option elements, those on asmSelect are optionally sortable with drag and drop (this part requires jQuery UI).

  * asmSelect hides, maintains and updates the original `<select multiple>` so that no changes are required to existing code.

  * If a user does not have javascript, then of course the regular `<select multiple>` form element is used instead.

  * If the original `<select multiple>` form element is modified by some other jQuery or javascript code, the change will be reflected in the asmSelect as well.

  * **[Try a Live Example](http://www.ryancramer.com/projects/asmselect/examples/example1.html)**

  * [Article about the advantages and disadvantages of this approach and others](http://www.ryancramer.com/journal/entries/select_multiple/)

# Forks of asmSelect #

  * [bsmSelect](http://github.com/vicb/bsmSelect)


# Requirements #

  * jQuery 1.2.6 or newer
  * An HTML/XHTML document that contains one or more `<select multiple>` form elements.


# Usage #

### Include jquery, asmSelect, and css in document head: ###

```

<script type="text/javascript" src="jquery.js"></script>
<script type="text/javascript" src="jquery.asmselect.js"></script>
<link rel="stylesheet" type="text/css" href="jquery.asmselect.css" />

```


### Use a jQuery selector in your document ready function: ###

```

$(document).ready(function() {
    $("select[multiple]").asmSelect();
}); 

```

If desired, you can specify options when you call the plugin:

```

$(document).ready(function() {
    $("select[multiple]").asmSelect({
        sortable: true,
        animate: true,
        addItemTarget: 'top'
    });
});

```

### To optionally set a label inside the select, set the title attribute: ###

```

<select name="cities" multiple="multiple" title="Please select a city">
...
</select>

```




# Options #

The following options may be specified using the format in the example directly above this section.

### Primary Options ###

  * **listType:**
    * Specify what type of list will be created as part of the asmSelect.
    * Allowed values: `'ol'` or `'ul'`
    * Default: `'ol'`

  * **sortable:**
    * May the user drag and drop to sort the list of elements they have selected?
    * Allowed values: `true` or `false`
    * Default: `false`
    * _Note: In order to use this option, you must have jQuery-UI Draggables, Droppables, and Sortables enabled._

  * **highlight:**
    * Show a quick highlight of what item was added or removed?
    * Allowed values: `true` or `false`
    * Default: `false`

  * **animate:**
    * Animate the adding or removing of items from the list?
    * Allowed values: `true` or `false`
    * Default: `false`

  * **hideWhenAdded:**
    * Stop showing in select after item has been added?
    * Allowed values: `true` or `false`
    * Default: `false`
    * _Note: Only functional in Firefox 3 at this time._

  * **addItemTarget:**
    * Where to place new selected items that are added to the list.
    * Allowed values: `'top'` or `'bottom'`
    * Default: `'bottom'`

  * **debugMode:**
    * Keeps original _select multiple_ visible so that you can monitor live changes made to it when debugging.
    * Default: `false`

### Text Labels ###

  * **removeLabel:**
    * Text used for the _remove_ link of each list item.
    * Default: `'remove'`

  * **highlightAddedLabel:**
    * Text that precedes highlight of item added.
    * Default: `'Added: '`

  * **highlightRemovedLabel:**
    * Text that precedes highlight of item removed.
    * Default: `'Removed: '`

### Modifiable CSS Classes ###

  * **containerClass:**
    * Class for container that wraps the entire asmSelect.
    * Default: `'asmContainer'`

  * **selectClass:**
    * Class for the newly created `<select>`.
    * Default: `'asmSelect'`

  * **listClass:**
    * Class for the newly created list of _listType_ (`ol` or `ul`).
    * Default: `'asmList'`

  * **listSortableClass:**
    * Another class given to the list when _sortable_ is active.
    * Default: `'asmListSortable'`

  * **listItemClass:**
    * Class given to the `<li>` list items.
    * Default: `'asmListItem'`

  * **listItemLabelClass:**
    * Class for the label text that appears in list items.
    * Default: `'asmListItemLabel'`

  * **removeClass:**
    * Class given to the _remove_ link in each list item.
    * Default: `'asmListItemRemove'`

  * **highlightClass:**
    * Class given to the highlight `<span>`.
    * Default: `'asmHighlight'`

# Known Issues #

  * In Firefox (all versions), if your form has an asmSelect that precedes radio buttons or checkboxes, then you should set Firefox's `autocomplete` to off. Otherwise, if the user manually reloads the page containing the form, it's possible for radio/checkbox values to be wrong. This is not an issue with asmSelect, but rather a general issue with Firefox and dynamic form fields. See this [issue report](http://code.google.com/p/jquery-asmselect/issues/detail?can=1&q=&colspec=ID%20Type%20Status%20Priority%20Milestone%20Owner%20Summary&sort=&id=5) for more information

  * The animating of adding/removing items is not as smooth in IE6/IE7 as it is in other browsers. There appears to be an [issue with jQuery slide effects](http://dev.jquery.com/ticket/3120) on list items with IE, so hopefully this will not be an issue forever. If you don't like the animation behavior in IE, I suggest setting animate to false. (false is the default)

  * In Safari 3 and Firefox 2, the 'add item' animation is not as smooth as in Firefox 3, though the removing is. Improvements need to be made here for more consistent animations across different browsers.

  * The `hideWhenAdded` option only works in Firefox 3 at this time. All other browsers continue to show the added items, but they are greyed out (disabled) and not selectable. This may in fact be preferable since the disabled items are placeholders.

  * In Internet Explorer, there is a slight gap between items that is not present in other browsers. Should be an easy fix with CSS, but haven't found it yet.

  * In Internet Explorer 6 (IE6), when dealing with a larger list of items, IE6 will sometimes do some odd scrolling within the select after an item is selected.

  * Also in IE6, when the list is sortable, the screen will flash every time you add an item. This appears to be getting triggered by the jQuery UI sortable("refresh") function that asmSelect calls.

# TODO #

  * Add user definable callback functions for add and remove

  * Make it possible for a selection in one asmSelect to alter the available options in another multiple select or regular select form field.

  * Set a limit for max number of selected items.

  * When the list is sortable, the items will take on a new look with something tactile to make it more obvious that they can be dragged.

  * Please [let me know](http://www.ryancramer.com/contact/) if you have any other suggestions.


# Please Note #

  * Disclaimer - This is a beta version, and as such is not intended for production use yet.

  * If you come across any bugs or issues, or if you see room for improvement in the way it works, or the underlying code, please [contact me](http://www.ryancramer.com/contact/).

  * As of July 15th, 2008, asmSelect has been confirmed to work properly with Firefox 2 & 3, Safari 3, IE6, IE7, and Opera 9.5. There are some issues with IE6. See Known Issues above.


_Copyright 2008, 2009, 2010 by Ryan Cramer_