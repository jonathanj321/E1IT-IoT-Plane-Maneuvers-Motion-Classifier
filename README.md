## <b>Airplane Maneuvers Motion Classifier</b>

Training is done to log the following flying maneuvers which are a sequence of 5 movements:

1. Descending right turn and level off: right-forward diagonal, left, back to neutral, back, forward
2. Ascending left turn and level off: back, left, right to neutral, forward, back to neutral
3. S turn into climb: left-back diagonal, right-forward diagonal , right-back diagonal, left, forward to neutral
4. Steep turn: right-back diagonal, left, forward-left diagonal, back, right to neutral
5. Right traffic pattern from takeoff: back, forward to neutral, right, left to neutral, forward
6. Left traffic pattern from landing: forward, back to neutral, left-back diagonal, right, forward to neutral

Then, these maneuvers are presented to the user in a random order and the user is asked to
perform them. Successful execution of each maneuver will result in a confirmation that the inputs
matched expected inputs. If the maneuver isn’t recognized, it will prompt the user to try again, or if
the user accidentally performed the wrong movement, it will tell the user that they performed the
wrong maneuver.

Data was acquired by performing 5 features for each of the 6 motions. If the velocity of the device
exceeded a certain threshold, feature 1 was set to the x axis velocity and feature 2 was set to the y axis
velocity.

The velocity was obtained by integrating the accelerometer output once over time with the following
approximations:
- Errors can occur if the device is not level, as the acceleration due to gravity will be projected onto the x and y axes, causing inaccurate readings.
- High-pass filters remove static acceleration from an angle deviation from level that is static.
- Low-pass filters remove high-frequency noise associated with varying friction forces.
- The processed data is passed to a softmax function and neural network, which classifies the sequence of movements as a specific motion.

