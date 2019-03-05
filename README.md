QFlashcard
===

QFlashcard is an `app extension` for [Quasar Framework v1](https://v1.quasar-framework.org/). It will not work with legacy versions of Quasar Framework.

This work is currently in `alpha` and there are expected changes while things get worked out.

# Installation
In your Quasar project:
```
quasar ext add @quasar/qflashcard
```

# Test Project
Can be found [here](https://github.com/hawkeye64/quasar-app-extension-qflashcard-test).

# Demo
Can be found [here](https://confident-wescoff-fb9e2c.netlify.com/#/).

# Example Code
This example mashes up the **nudge**, **fade-in**, **drop-down** and **drop-up** transitions.

```
<q-flashcard :style="style">
  <q-flashcard-section transition="nudge">
    <img src="statics/2.jpg" width=300 height=200>
  </q-flashcard-section>
  <q-flashcard-section transition="fade-in" style="width:100%;bottom:20px;top:0;background-color: rgba(219,127,8, 0.7);">
    <q-flashcard-section transition="drop-down" class="text-center my-header">
      Combo Demo #1
    </q-flashcard-section>
    <q-flashcard-section transition="drop-up" class="my-text">
      For beautiful eyes, look for the good in others; for beautiful lips, speak only words of kindness; and for poise, walk with the knowledge that you are never alone.
    </q-flashcard-section>
    <q-flashcard-section transition="fade-in" class="my-button-container">
      <a href="#" class="my-button">Learn More</a>
    </q-flashcard-section>
  </q-flashcard-section>
</q-flashcard>

```
where **style** for the QFlashcard is defined as:
```
computed: {
  style () {
    return {
      width: '320px',
      height: '220px',
      backgroundImage: 'url(../statics/bgimg.jpg)',
      padding: '10px',
      border: '10px solid #fff',
      textAlign: 'center',
      boxShadow: '1px 1px 2px #e6e6e6'
    }
  }
}
```

# QFlashcard
QFlashcard has no properties, events or methods. It has a single "default" slot. It expects one or more QFlashcardSection components to fill the slot.

# QFlashcardSection Vue Properties
| Vue&nbsp;Property | Type	| Description |
|---|---|---|
| type | String | The type of transition to use (listed below) |

QFlashcardSection has no events or methods. It has a single "default" slot. You can put anything into this slot.

# Transitions
The list of currently available transitions are as follows:

| Transition name |
|---|
| fade-in |
| fade-out |
| flip-left |
| flip-right |
| flip-down |
| flip-up |
| nudge |
| shake-left |
| shake-right |
| shake-down |
| shake-up |
| slide-in-left |
| slide-in-right |
| slide-in-down |
| slide-in-up |
| slide-out-left |
| slide-out-right |
| slide-out-down |
| slide-out-up |
| spin-in |
| spin-out |
| zoom-in |
| zoom-out |


# Questions
- Q. Can I use my own transitions?
- A. Yes, you can! Make your transition and the styling must be prefixed with `fc-`, for example `.fc-my-transition` and then for the `transition` property of `QFlashcardSection` call it like this: `transition="my-transition"`. The `fc-` is automatically prefixed to the tansition name. However, it must fall under the `.q-flashcard` namespace, as in:
  ```
  .q-flashcard .fc-my-transition {
    /* attribuutes */
  }
  ```
  This is so the transition only works while in a QFlashcard area as these transitons should not be used with other elements/compnents.
- Q. Why prefix with `'fc-'`?
- A. This is to avoid name style collisions. Having a transition called `.slide-out` would be too generic. Having `.fc-slide-out` is more deterministic.