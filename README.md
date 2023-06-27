# Get Current address using Javascript Code
We can use browser nagivigator to get current location.
And using that location's latitude and longitude we invoke the openstreetmap api to get current address.

```javascript
navigator.geolocation.getCurrentPosition((position) => {
  const { latitude, longitude } = position.coords;
  const url = `https://nominatim.openstreetmap.org/reverse?format=json&lat=${latitude}&lon=${longitude}`;
  fetch(url)
    .then((res) => res.json())
    .then((data) => {
      console.log(data.display_name);
      console.table(data.address);
    })
    .catch(() => console.error("Error on fetching data."));
});
```
