# react-native-image-cropper

This Image cropper is based on the gl-react-native [library](https://github.com/ProjectSeptemberInc/gl-react-native)

![Cropping View](https://media.giphy.com/media/l46CDga4bxZccVxWU/giphy.gif)

## Requirements
- `gl-react` You need to install gl-react. `npm i -S gl-react` 
- `gl-react-native` You need to install gl-react-native and link the repo in RN. `npm i -S gl-react-native & rnpm link` 
- `react-native` Android requires you to have RN 0.28 or higher!

#### `{ImageCrop}` Props

- `image` **(required)**: link to image that should be cropped.
- `cropHeight` **(required)**: height of the image in cropped size.
- `cropWidth` **(required)**: width of the image in cropped size.
- `zoom`: range 0 - 100 setting zoom value. where 100 = full zoom. (default: 0)
- `maxZoom`: max zoom value, should be bigger than minZoom value (default: 100)
- `minZoom`: min zoom value, should be smaller than maxZoom value (default: 0) 
- `panToMove`: Use pan to move image? (default: true)
- `pinchToZoom` Use pinch to zoom image? (default: true)
- `quality`: a value from 0 to 1 to describe the quality of the snapshot. 0 means 0% (most compressed) and 1 means 100% (best quality). (default: 1)
- `type`: the file type default value is **"png"**, **"jpg"** is also supported. Refer to implementations to see more supported values. (default: jpg)
- `format`: **"file"** or **"base64"**. Default is **"base64"**
- `filePath`: If format is **"file"** then filePath is required. 


#### `{ImageCrop}` Functions
- `crop()`: returns either a base64 encoded image or a file uri.


## Example
```js

render() {
  return (
  <View>
    <ImageCrop 
      ref={'cropper'}
      image={this.state.image}
      cropHeight={this.state.height}
      cropWidth={this.state.width}
      zoom={this.state.zoom}
      maxZoom={80}
      minZoom={20}
      panToMove={true}
      pinchToZoom={true}
    />
    <Text onPress={this.capture()}>Capture()</Text>
  </View>
    
  )
} 
capture(){
  this.refs.cropper.crop()
  .then(base64 => console.log(base64))
}

```
