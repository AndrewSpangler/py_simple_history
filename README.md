# py_simple_history 0.0.1<a name="mark0"></a>

***A super basic python History Tracking object***

---

- [About](#mark1)
- [Installation](#mark2)
- [Usage](#mark3)
	- [history_mixin](#mark4)
- [Example](#mark5)

---

# About<a name="mark1"></a>[^](#mark0)

In this instance "History" means the state of an object at any given time. This module aims to provide a simple interface for tracking and moving through histories.

# Installation<a name="mark2"></a>[^](#mark0)

Available on pip - `pip install py_simple_history`

# Usage<a name="mark3"></a>[^](#mark0)

### history_mixin<a name="mark4"></a>[^](#mark3)
> **Abstract mixin to add simple history-tracking to an object.**
> 
> ```py
> class history_mixin(object):
> 	def __init__(self, start_data):
> 		...
> 	def add_history(self, data):
> 		"""Add a history point. Clears any undone data history points."""
> 	def clear_history(self, data=None):
> 		"""Clears history. Sets a new history point, if no data specified uses the current data point."""
> 	def redo(self):
> 		"""Redoes history one step if possible."""
> 	def undo(self):
> 		"""Undoes history one step if possible."""
> ```
### Example<a name="mark5"></a>[^](#mark0)

> ```py
> from py_simple_history import history_mixin
> 
> class demo_object(history_mixin):
>     def __init__(self, initial_data):
>         history_mixin.__init__(self, initial_data)
>         self.load(self.data:=initial_data)
>         ...
> 
>     def on_update(self, new_data):
>         self.add_history(new_data)
>         self.load(data)
> 
>     def load(self, data):
>         self.data = data
> 
>     def step_back(self):
>         self.load(self.undo())
> 
>     def step_forward(self):
>         self.load(self.redo())
> ```
