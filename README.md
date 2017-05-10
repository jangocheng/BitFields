# BitFields

NuGet Package: https://www.nuget.org/packages/BitFields/

The analyzer in this package currently does not support `packages.config` format.

## N-bit Ingeters

![N-bit integers](docs/bitn.png)

## Bit-field Generator

Type definition:

```cs
struct Rgb555
{
    enum BitFields
    {
        B = 5,
        G = 5,
        R = 5,
    }
}
```

Quick Action:

![Quick Action to generate bit-fields](docs/bitfieldgenerator.png)

Generated code:

```cs
using BitFields;

partial struct Rgb555
{
    public ushort Value;

    private const int BShift = 0;
    private const ushort BMask = unchecked((ushort)((1U << 5) - (1U << 0)));
    public Bit5 B
    {
        get => (Bit5)((Value & BMask) >> BShift);
        set => Value = unchecked((ushort)((Value & ~BMask) | ((((ushort)value) << BShift) & BMask)));
    }
    private const int GShift = 5;
    private const ushort GMask = unchecked((ushort)((1U << 10) - (1U << 5)));
    public Bit5 G
    {
        get => (Bit5)((Value & GMask) >> GShift);
        set => Value = unchecked((ushort)((Value & ~GMask) | ((((ushort)value) << GShift) & GMask)));
    }
    private const int RShift = 10;
    private const ushort RMask = unchecked((ushort)((1U << 15) - (1U << 10)));
    public Bit5 R
    {
        get => (Bit5)((Value & RMask) >> RShift);
        set => Value = unchecked((ushort)((Value & ~RMask) | ((((ushort)value) << RShift) & RMask)));
    }
}
```
