---
title: Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)
description: Dowiedz się, jak używać atrybutów, aby dostosować sposób, w jaki struktury są ułożone w pamięci w języku C#. Ten przykład implementuje odpowiednik Unii z C/C++.
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925075"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Jak utworzyć Unię C/C++ za pomocą atrybutów (C#)

Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci. Na przykład, można utworzyć elementy znane jako Unia w C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` `FieldOffset` atrybutów i.

## <a name="example"></a>Przykład

W tym segmencie kodu wszystkie pola, które są `TestUnion` uruchamiane w tej samej lokalizacji w pamięci.

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a>Przykład

Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

Dwa pola liczb całkowitych `i1` i `i2` , współużytkują te same lokalizacje pamięci co `lg` . Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku C#](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](index.md)
- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)
