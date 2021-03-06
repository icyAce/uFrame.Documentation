# Type References

_Type Reference_ is a node type that allows you to specify a new type that you can use in other nodes. No class file will be generated by uFrame for the created type. You have to create it yourself.

For example, you can create your custom class `LevelDescriptor` and then use the _Type Reference_ node to specify the type of the `CurrentLevel` property.

![](images/screenshot_112.png)

```csharp
/*
 * This class holds information about level. We have made it monobehavior,
 * since we wanted to introduce an example of in-game db based on monobehaviours.
 * If you use another source of data, you can simply remove the monobeh inharitance.
 */
//Remove monobehaviour inheritance to use LevelDescriptor outside of unity
public class LevelDescriptor : MonoBehaviour
{
    public int Id;
    public string Title;
    public string Description;
    public string LevelScene;
    public bool IsLocked;
}
```

Other application of _Type References_ is to use them as handlers in services.

[picture of a service node with a handler and a Type Reference node]

[description of the picture above]

## External Assembly References

In some instances where your types come from an external assembly you would need to tell the generator how to access the type.

To do this you need to:

1) Create an editor folder in your uframe project
2) Create a new plugin file, i.e. MyProjectPlugin.cs
3) Make the plugin extend from `DiagramPlugin`
4) Override the `Initialize` method
5) Add the line ` InvertApplication.CachedAssemblies.Add(typeof (MyType).Assembly);`

This will tell the code gen where to find your types when using external assemblies.
