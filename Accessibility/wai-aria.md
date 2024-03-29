# WAI-ARIA

**WAI-ARIA(Web Accessibility Initiative - Accessible Rich Internet Applications)** is a technology that can help with
such problems by adding in further semantics that browsers and assistive technologies can recognize and let users know
what is going on.

Spec written by W3C, defining a set of additional HTML attributes that can be applied to elements to provide additional
semantics and improve accessibility.

#### Three main features:

- **Roles**: These define <span style="color: #009988">what an element is or does</span>
  e.g. `role="navigation" (<nav>)`
  or `role="complementary" (<aside>)`, but there are also others that describe different pages structures, such
  as `role="banner"`, `role="search"`, `role="
  tabgroup"`, `role="tab"`, etc., which are commonly found in UIs.


- **Properties**: These define properties of elements, which can be used to <span style="color: #009988">give them extra
  meaning</span> or semantics. As an example, `aria-required="true"` specifies that a form input needs to be filled in
  order to be valid or
  `aria-labelledby="label"` allows you to put an ID on an element, then reference it as being the label for anything
  else on the page.


- **States**: Special properties that <span style="color: #009988">define the current state/condition of elements</span>
  , such as `aria-disabled="true"`

## When should you use WAI-ARIA?

We talked about some problems that prompted WAI-ARIA to be created earlier on, but essentially, there are four main
areas that WAI-ARIA is useful in:

1. **Signposts/Landmarks**: ARIA's role attribute values can act as landmarks that either replicate the semantics of
   HTML5 elements (e.g. `<nav>`), or go beyond HTML5 semantics to provide signposts to different functional areas, e.g
   `search, tabgroup, tab, listbox`, etc.


2. **Dynamic content updates**: Screenreaders tend to have difficulty with reporting constantly changing content; with
   ARIA we can use `aria-live` to inform screenreader users when an area of content is updated, e.g. via XMLHttpRequest,
   or DOM APIs.
   `aria-live` attribute value can be of three types:
    - **off**: The default. Updates should not be announced.
    - **polite**: Updates should be announced only if the user is idle.
    - **assertive**: Updates should be announced to the user as soon as possible.


3. **Enhancing keyboard accessibility**: There are built-in HTML elements that have native keyboard accessibility; when
   other elements are used along with JavaScript to simulate similar interactions, keyboard accessibility and
   screenreader reporting suffers as a result. Where this is unavoidable, WAI-ARIA provides a means to allow other
   elements to receive focus (using `tabindex`).


4. **Accessibility of non-semantic controls**: When a series of nested `<div>`s along with CSS/JavaScript is used to
   create a complex UI-feature, or a native control is greatly enhanced/changed via JavaScript, accessibility can suffer
   — screenreader users will find it difficult to work out what the feature does if there are no semantics or other
   clues. In these situations, ARIA can help to provide what's missing with a combination of roles
   like `button, listbox, or tabgroup`, and properties like `aria-required` or `aria-posinset` to provide further clues
   as to functionality.
