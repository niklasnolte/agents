<div itemscope itemtype="http://developers.google.com/ReferenceObject">
<meta itemprop="name" content="tf_agents.policies.random_tf_policy.RandomTFPolicy" />
<meta itemprop="path" content="Stable" />
<meta itemprop="property" content="action_spec"/>
<meta itemprop="property" content="emit_log_probability"/>
<meta itemprop="property" content="info_spec"/>
<meta itemprop="property" content="name"/>
<meta itemprop="property" content="name_scope"/>
<meta itemprop="property" content="policy_state_spec"/>
<meta itemprop="property" content="policy_step_spec"/>
<meta itemprop="property" content="submodules"/>
<meta itemprop="property" content="time_step_spec"/>
<meta itemprop="property" content="trainable_variables"/>
<meta itemprop="property" content="trajectory_spec"/>
<meta itemprop="property" content="__init__"/>
<meta itemprop="property" content="action"/>
<meta itemprop="property" content="distribution"/>
<meta itemprop="property" content="get_initial_state"/>
<meta itemprop="property" content="update"/>
<meta itemprop="property" content="variables"/>
<meta itemprop="property" content="with_name_scope"/>
</div>

# tf_agents.policies.random_tf_policy.RandomTFPolicy

<table class="tfo-notebook-buttons tfo-api" align="left">
</table>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/random_tf_policy.py">View
source</a>

## Class `RandomTFPolicy`

Returns random samples of the given action_spec.

Inherits From: [`Base`](../../../tf_agents/policies/tf_policy/Base.md)

<!-- Placeholder for "Used in" -->


<h2 id="__init__"><code>__init__</code></h2>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

```python
__init__(
    time_step_spec,
    action_spec,
    policy_state_spec=(),
    info_spec=(),
    clip=True,
    emit_log_probability=False,
    automatic_state_reset=True,
    name=None
)
```

Initialization of Base class.

#### Args:

*   <b>`time_step_spec`</b>: A `TimeStep` spec of the expected time_steps.
    Usually provided by the user to the subclass.
*   <b>`action_spec`</b>: A nest of BoundedTensorSpec representing the actions.
    Usually provided by the user to the subclass.
*   <b>`policy_state_spec`</b>: A nest of TensorSpec representing the
    policy_state. Provided by the subclass, not directly by the user.
*   <b>`info_spec`</b>: A nest of TensorSpec representing the policy info.
    Provided by the subclass, not directly by the user.
*   <b>`clip`</b>: Whether to clip actions to spec before returning them.
    Default True. Most policy-based algorithms (PCL, PPO, REINFORCE) use
    unclipped continuous actions for training.
*   <b>`emit_log_probability`</b>: Emit log-probabilities of actions, if
    supported. If True, policy_step.info will have CommonFields.LOG_PROBABILITY
    set. Please consult utility methods provided in policy_step for setting and
    retrieving these. When working with custom policies, either provide a
    dictionary info_spec or a namedtuple with the field 'log_probability'.
*   <b>`automatic_state_reset`</b>: If `True`, then `get_initial_policy_state`
    is used to clear state in `action()` and `distribution()` for for time steps
    where `time_step.is_first()`.
*   <b>`name`</b>: A name for this module. Defaults to the class name.

## Properties

<h3 id="action_spec"><code>action_spec</code></h3>

Describes the TensorSpecs of the Tensors expected by `step(action)`.

`action` can be a single Tensor, or a nested dict, list or tuple of
Tensors.

#### Returns:

An single BoundedTensorSpec, or a nested dict, list or tuple of
`BoundedTensorSpec` objects, which describe the shape and
dtype of each Tensor expected by `step()`.

<h3 id="emit_log_probability"><code>emit_log_probability</code></h3>

Whether this policy instance emits log probabilities or not.

<h3 id="info_spec"><code>info_spec</code></h3>

Describes the Tensors emitted as info by `action` and `distribution`.

`info` can be an empty tuple, a single Tensor, or a nested dict,
list or tuple of Tensors.

#### Returns:

An single TensorSpec, or a nested dict, list or tuple of
`TensorSpec` objects, which describe the shape and
dtype of each Tensor expected by `step(_, policy_state)`.

<h3 id="name"><code>name</code></h3>

Returns the name of this module as passed or determined in the ctor.

NOTE: This is not the same as the `self.name_scope.name` which includes
parent module names.

<h3 id="name_scope"><code>name_scope</code></h3>

Returns a `tf.name_scope` instance for this class.

<h3 id="policy_state_spec"><code>policy_state_spec</code></h3>

Describes the Tensors expected by `step(_, policy_state)`.

`policy_state` can be an empty tuple, a single Tensor, or a nested dict,
list or tuple of Tensors.

#### Returns:

An single TensorSpec, or a nested dict, list or tuple of
`TensorSpec` objects, which describe the shape and
dtype of each Tensor expected by `step(_, policy_state)`.

<h3 id="policy_step_spec"><code>policy_step_spec</code></h3>

Describes the output of `action()`.

#### Returns:

A nest of TensorSpec which describe the shape and dtype of each Tensor
emitted by `action()`.

<h3 id="submodules"><code>submodules</code></h3>

Sequence of all sub-modules.

Submodules are modules which are properties of this module, or found as
properties of modules which are properties of this module (and so on).

```
a = tf.Module()
b = tf.Module()
c = tf.Module()
a.b = b
b.c = c
assert list(a.submodules) == [b, c]
assert list(b.submodules) == [c]
assert list(c.submodules) == []
```

#### Returns:

A sequence of all submodules.

<h3 id="time_step_spec"><code>time_step_spec</code></h3>

Describes the `TimeStep` tensors returned by `step()`.

#### Returns:

A `TimeStep` namedtuple with `TensorSpec` objects instead of Tensors,
which describe the shape, dtype and name of each tensor returned by
`step()`.

<h3 id="trainable_variables"><code>trainable_variables</code></h3>

Sequence of variables owned by this module and it's submodules.

Note: this method uses reflection to find variables on the current instance
and submodules. For performance reasons you may wish to cache the result
of calling this method if you don't expect the return value to change.

#### Returns:

A sequence of variables for the current module (sorted by attribute
name) followed by variables from all submodules recursively (breadth
first).

<h3 id="trajectory_spec"><code>trajectory_spec</code></h3>

Describes the Tensors written when using this policy with an environment.

#### Returns:

A `Trajectory` containing all tensor specs associated with the
observation_spec, action_spec, policy_state_spec, and info_spec of
this policy.

## Methods

<h3 id="action"><code>action</code></h3>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

``` python
action(
    time_step,
    policy_state=(),
    seed=None
)
```

Generates next action given the time_step and policy_state.

#### Args:

*   <b>`time_step`</b>: A `TimeStep` tuple corresponding to `time_step_spec()`.
*   <b>`policy_state`</b>: A Tensor, or a nested dict, list or tuple of Tensors
    representing the previous policy_state.
*   <b>`seed`</b>: Seed to use if action performs sampling (optional).

#### Returns:

A `PolicyStep` named tuple containing:
  `action`: An action Tensor matching the `action_spec()`.
  `state`: A policy state tensor to be fed into the next call to action.
  `info`: Optional side information such as action log probabilities.

#### Raises:

* <b>`RuntimeError`</b>: If subclass __init__ didn't call super().__init__.

<h3 id="distribution"><code>distribution</code></h3>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

``` python
distribution(
    time_step,
    policy_state=()
)
```

Generates the distribution over next actions given the time_step.

#### Args:

*   <b>`time_step`</b>: A `TimeStep` tuple corresponding to `time_step_spec()`.
*   <b>`policy_state`</b>: A Tensor, or a nested dict, list or tuple of Tensors
    representing the previous policy_state.

#### Returns:

A `PolicyStep` named tuple containing:

  `action`: A tf.distribution capturing the distribution of next actions.
  `state`: A policy state tensor for the next call to distribution.
  `info`: Optional side information such as action log probabilities.

<h3 id="get_initial_state"><code>get_initial_state</code></h3>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

``` python
get_initial_state(batch_size)
```

Returns an initial state usable by the policy.

#### Args:

* <b>`batch_size`</b>: The batch shape.


#### Returns:

A nested object of type `policy_state` containing properly
initialized Tensors.

<h3 id="update"><code>update</code></h3>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

``` python
update(
    policy,
    tau=1.0,
    sort_variables_by_name=False
)
```

Update the current policy with another policy.

This would include copying the variables from the other policy.

#### Args:

*   <b>`policy`</b>: Another policy it can update from.
*   <b>`tau`</b>: A float scalar in [0, 1]. When tau is 1.0 (default), we do a
    hard update.
*   <b>`sort_variables_by_name`</b>: A bool, when True would sort the variables
    by name before doing the update.

#### Returns:

An TF op to do the update.

<h3 id="variables"><code>variables</code></h3>

<a target="_blank" href="https://github.com/tensorflow/agents/tree/master/tf_agents/policies/tf_policy.py">View
source</a>

``` python
variables()
```

Returns the list of Variables that belong to the policy.

<h3 id="with_name_scope"><code>with_name_scope</code></h3>

``` python
with_name_scope(
    cls,
    method
)
```

Decorator to automatically enter the module name scope.

```
class MyModule(tf.Module):
  @tf.Module.with_name_scope
  def __call__(self, x):
    if not hasattr(self, 'w'):
      self.w = tf.Variable(tf.random.normal([x.shape[1], 64]))
    return tf.matmul(x, self.w)
```

Using the above module would produce `tf.Variable`s and `tf.Tensor`s whose
names included the module name:

```
mod = MyModule()
mod(tf.ones([8, 32]))
# ==> <tf.Tensor: ...>
mod.w
# ==> <tf.Variable ...'my_module/w:0'>
```

#### Args:

* <b>`method`</b>: The method to wrap.


#### Returns:

The original method wrapped such that it enters the module's name scope.
