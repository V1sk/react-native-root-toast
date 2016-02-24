### react-native-root-toast

-----------------------

#### Features
1. Pure javascript solution.
2. Support both Android and iOS.
3. Lots of custom options for Toast.
4. You can show/hide Toast by calling api or using Component inside render.

### Install

`npm install react-native-root-toast`


### Settings

Name                | Default                  |  Type    | Description
--------------------|--------------------------|----------|---------------------------
duration            | Toast.durations.SHORT    | Number   | The duration of the toast. (Only for api calling method)
visible             | false                    | Bool     | The visibility of toast. (Only for Toast Component)
position            | Toast.positions.BOTTOM   | Number   | The position of toast showing on screen (A negative number represents the distance from the bottom of screen. A positive number represents the distance form the top of screen. `0` will position the toast to the middle of screen.)
animation           | true                     | Bool     | Should preform an animation on toast appearing or disappearing.
shadow              | true                     | Bool     | Should drop shadow around Toast element.
delay               | 0                        | Number   | The delay duration before toast start appearing on screen.
onShow              | null                     | Function | Callback for toast\`s appear animation start
onShown             | null                     | Function | Callback for toast\`s appear animation end
onHide              | null                     | Function | Callback for toast\`s hide animation start
onHidden            | null                     | Function | Callback for toast\`s hide animation end


### Properties

### Usage

There are two different ways to manage a Toast.

##### **Calling api**

```
import Toast from 'react-native-root-toast';


// Add a Toast on screen.
let toast = Toast.show('This is a message', {
    duration: Toast.durations.LONG,
    position: Toast.positions.BOTTOM,
    shadow: true,
    animation: true,
    hideOnPress: true,
    delay: 0,
    onShow: () => {
        // calls on toast\`s appear animation start
    },
    onShown: () => {
        // calls on toast\`s appear animation end.
    },
    onHide: () => {
        // calls on toast\`s hide animation start.
    },
    onHidden: () => {
        // calls on toast\`s hide animation end.
    }
});

// You can manually hide the Toast, or it will automatically disappear after a `duration` ms timeout.
setTimeout(function () {
    Toast.hide(toast);
}, 500);

```

##### **Using a Component**

```
import React, {Component} from 'react-native';
import Toast from 'react-native-root-toast';

class Example extends Component{
    constructor() {
        super(...arguments);
        this.state = {
            visible: false
        };
    }

    componentDidMount() {
        setTimeout(() => this.setState({
            visible: true
        }), 2000); // show toast after 2s

        setTimeout(() => this.setState({
            visible: false
        }), 5000); // hide toast after 5s
    };

    render() {
        return <Toast
            visible={this.state.visible}
            position={50}
            shadow={false}
            animation={false}
            hideOnPress={true}
        >This is a message</Toast>;
    }
}

```
