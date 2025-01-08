# ngx-google-address-autocomplete

An Angular package that provides Google Places Autocomplete functionality for input fields, making it easy to implement address autocomplete in your Angular applications.

## Installation

`npm install ngx-google-address-autocomplete`

## Setup

### 1\. Add Google Maps JavaScript API

Add the Google Maps JavaScript API script to your `index.html` file:


`<script src="https://maps.googleapis.com/maps/api/js?key=<Your API KEY>&libraries=places"></script>`

Replace `<Your API KEY>` with your actual Google Maps API key.

### 2\. Import Module

Import the `NgxGoogleAddressAutocompleteModule` in your app module:

typescript

Copy

``` 
import { NgxGoogleAddressAutocompleteModule } from "ngx-google-address-autocomplete";

@NgModule({
  imports: [
    NgxGoogleAddressAutocompleteModule,
    BrowserModule,
    FormsModule,
    // ... other modules
  ],
  // ... other module configurations
})
export class AppModule { }
```

## Usage

Add the directive to your input field:

```
<input 
  ngx-google-address-autocomplete
  [options]="options"
  #placesRef="ngx-places"
  (onAddressChange)="handleAddressChange($event)"
/>
```

### Options

You can customize the behavior of the autocomplete by passing options:

## Country Restriction

To restrict address suggestions to a specific country:

```
<input 
  ngx-google-address-autocomplete
  [options]="{
    types: [],
    componentRestrictions: { country: 'UA' }
  }"
  #placesRef="ngx-places"
  (onAddressChange)="handleAddressChange($event)"
/>
```

## API Reference

### Directive

*   `ngx-google-address-autocomplete`: Main directive to enable address autocomplete

### Inputs

*   `[options]`: Configuration object for Google Places Autocomplete
    *   `types`: Array of place types
    *   `componentRestrictions`: Object to restrict results to specific countries

### Outputs

*   `(onAddressChange)`: Event emitted when an address is selected, returns the Google Place result

### Template Reference

*   `#placesRef="ngx-places"`: Reference to access the directive instance

## Example


```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  template: `
    <input 
      ngx-google-address-autocomplete
      [options]="options"
      #placesRef="ngx-places"
      (onAddressChange)="handleAddressChange($event)"
    />
  `
})
export class AppComponent {
  options = {
    types: [],
    componentRestrictions: { country: 'UA' }
  };

  handleAddressChange(address: any) {
    console.log(address);
  }
}
```

## License

MIT

## Contributing

Feel free to submit issues and enhancement requests!