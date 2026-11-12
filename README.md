# Coffee Counter: a SwiftUI bug hunt

Coffee Counter is a small iPhone app for taking coffee orders. It's also broken.
Someone wrote it in a hurry and made the kinds of mistakes every developer makes.
Your job is to get it building, then get it working correctly.

Every bug is tied to something in these two chapters of *The Swift Programming Language*:

- [The Basics](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/thebasics)
- [Basic Operators](https://docs.swift.org/swift-book/documentation/the-swift-programming-language/basicoperators)

## Setup

1. Open `CoffeeCounter.xcodeproj` in **Xcode 16 or newer**.
2. Pick any iPhone simulator at the top of the window.
3. Press **⌘B** to build. It will fail. That's the point.

You only need the three `.swift` files in the `CoffeeCounter` folder:
`CoffeeCounterApp.swift`, `CoffeeOrder.swift`, and `ContentView.swift`.

## Level 1: make it build

There are **16 compile errors** across two files (Xcode's count will jump around while you work).

How real developers handle this:

- Open the **Issue navigator** (⌘5) to see every error in one list.
- **Fix the first error first**, then build again. One mistake can cause a pile of
  errors further down, and those disappear once the real cause is fixed.
- **Read the whole error message.** Swift's messages usually say exactly what's wrong,
  and many include a "Fix" button. Before you click it, make sure you understand *why*
  it's suggesting that, because the quick fix isn't always the right fix.
- Don't delete code to make an error go away. Make the code do what it was meant to do.

## Level 2: make it correct

Once it builds, press **⌘R** to run it. Hidden bugs show up now: crashes and wrong
answers. When the app crashes, Xcode stops on the line that caused it and shows the
reason in red. Read it.

Use this spec to test the app. If the app disagrees with the spec, that's a bug.

| Feature | Expected behavior |
|---|---|
| Launch | The app opens without crashing, with an empty order. |
| Greeting | Shows a friendly prompt when there's no name, and "Hi, *name*!" once a name is typed. |
| Adding items | Typing a whole number and tapping **Add to order** adds that many. Typing something like `two` or leaving it blank must **not** crash; show a message instead. Zero or negative amounts shouldn't be added. |
| Item count | "1 item", "2 items", "7 items", and so on. |
| Tax | 8% of the subtotal. |
| Tip | 10%, 15%, or 20% of the subtotal. A $10.00 subtotal with 15% tip shows a $1.50 tip. |
| Discount | `WELCOME10` takes 10% off, **only when the subtotal is over $10**. |
| Limits | Max per order: Espresso 6, Latte 4, Cold Brew 4, Muffin 10. Ordering *exactly* the max is allowed. |
| Validation | Placing an order with no name, no items, or too many of something shows a clear message and does **not** place the order. |
| Free orders | Every 5th order (5, 10, 15…) is on the house. Other orders are not. |
| Loyalty | Each order earns 50 points. The app must not crash no matter how many orders you place. |
| Status message | Money is shown like `$12.34`, not `12.340000000000002`. |

**Tip:** Some Level 2 bugs only appear *because* of how you fixed a Level 1 error.
That's realistic. A fix that makes the compiler happy isn't always correct.

## Stuck?

- `HINTS.md` gives a nudge for each bug without the answer.
- `SOLUTIONS.md` has every bug explained and fixed. Try hard before opening it.
