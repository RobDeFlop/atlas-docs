---
description: Learn more about the available ClientDecorators
---

# Client

## Basic Event Decorator

{% hint style="info" %}
Every basic event decorator has an optional parameter. If this parameter is not provided, the name of the decorated method will be used as the event name.
{% endhint %}

{% tabs %}
{% tab title="@OnServer" %}
```typescript
@OnServer('customEventname')
public doFancyStuff(player: Player): void {
  // customEventname is the eventname for listen
}

@OnServer()
public youAwesomMethod(player: Player): void {
  // yourAwesomeMethod is the eventname for listen
}
```
{% endtab %}

{% tab title="@OnceServer" %}
```typescript
@OnceServer('customEventname')
public doFancyStuff(player: Player): void {
  // customEventname is the eventname for listen
}

@OnceServer()
public youAwesomMethod(player: Player): void {
  // yourAwesomeMethod is the eventname for listen
}
```
{% endtab %}

{% tab title="@OnGui" %}
```typescript
@OnGui('customEventname')
public doFancyStuff(player: Player): void {
  // customEventname is the eventname for listen
}

@OnGui()
public youAwesomMethod(player: Player): void {
  // yourAwesomeMethod is the eventname for listen
}
```
{% endtab %}
{% endtabs %}

## Key Event Decorators

Working with key events can be very confusing. The following decorators might help you while you can focus on the funny part.

{% hint style="info" %}
Key Event Decorators has one parameter, number or first char from the name of the key
{% endhint %}

{% tabs %}
{% tab title="@KeyUp" %}
```typescript
@KeyUp('E')
public doSomething(): void {
    // Do something after release E key
}

@KeyUp(69) // E Key
public doSomething(): void {
    // Do something after release E key
}
```
{% endtab %}

{% tab title="@KeyDown" %}
```typescript
@KeyDown('E')
public doSomething(): void {
    // Do something after pressing E key
}

@KeyDown(69) // E Key
public doSomething(): void {
    // Do something after pressing E key
}
```
{% endtab %}
{% endtabs %}

## GameEntity Decorators

Interacting with the game entity events like \(**gameEntityCreate** and **gameEntityDestroy**\) can be really annoying.  
The framework helps you a lot with this. Don't worry, only one event listener will be created for these decorators.  
You can use as many as you want without performance issues.

{% hint style="warning" %}
First parameter is a typeof [BaseObjectType](https://docs.altv.mp/js/api/alt-client.BaseObjectType.html#fields).
{% endhint %}

{% tabs %}
{% tab title="@GameEntityCreate" %}
```typescript
@GameEntityCreated(BaseObjectType.Player)
public doSomething(entity: Player): void {
    // You don't need to check the instance of the entity to fit your needs
    // the decorator does this job for you
}
```
{% endtab %}

{% tab title="@GameEntityDestroy" %}
```typescript
@GameEntityDestroy(BaseObjectType.Player)
public doSomething(entity: Player): void {
    // You don't need to check the instance of the entity to fit your needs
    // the decorator does this job for you
}
```
{% endtab %}
{% endtabs %}

## MetaChange Decorators

Working with MetaChange \(**StreamSyncedMetaChange** and **SyncedMetaChange**\) is one of the most annoying part while developing. These decorators will help you a lot. No headache, no brainfuck, it will work as you expect.

{% hint style="warning" %}
First parameter is a typeof [BaseObjectType](https://docs.altv.mp/js/api/alt-client.BaseObjectType.html#fields).
{% endhint %}

{% tabs %}
{% tab title="@SyncedMetaChange" %}
```typescript
@SyncedMetaChange(BaseObjectType.Player)
public doSomethingSpecial(
    entity: Player, 
    key: string, 
    newValue: any, 
    oldValue: any
): void {
    // Working with any meta change for a player entity
    // Check for key you want
}

@SyncedMetaChange(BaseObjectType.Player, 'yourKey')
public doSomethingSpecial(entity: Player, newValue: any, oldValue: any): void {
    // Working with any meta change for a player entity
    // Only called if the yourKey is triggered.
    // you can do directly working with the value and create clean code
}
```
{% endtab %}

{% tab title="@StreamSyncedMetaChange" %}
```typescript
@StreamSyncedMetaChange(BaseObjectType.Player)
public doSomethingSpecial(
    entity: Player, 
    key: string, 
    newValue: any, 
    oldValue: any
): void {
    // Working with any meta change for a player entity
    // Check for key you want
}

@StreamSyncedMetaChange(BaseObjectType.Player, 'yourKey')
public doSomethingSpecial(entity: Player, newValue: any, oldValue: any): void {
    // Working with any meta change for a player entity
    // Only called if the yourKey is triggered.
    // you can do directly working with the value and create clean code
}
```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
If you use the second parameter as your key, please notice that this key won't be able to use inside the method parameter map anymore.
{% endhint %}

