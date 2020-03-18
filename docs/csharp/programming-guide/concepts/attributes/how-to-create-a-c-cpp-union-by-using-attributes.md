---
title: Jak utworzyć związek C/C++ przy użyciu atrybutów (C#)
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: ff8ce560444581a28b257820573224f89a274cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141576"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>Jak utworzyć związek C/C++ przy użyciu atrybutów (C#)

Za pomocą atrybutów, można dostosować sposób struktur są rozmieszczone w pamięci. Na przykład można utworzyć, co jest znane jako unii w `StructLayout(LayoutKind.Explicit)` Języku C++ przy użyciu i `FieldOffset` atrybutów.

## <a name="example"></a>Przykład

W tym segmencie kodu wszystkie `TestUnion` pola start w tej samej lokalizacji w pamięci.

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

Poniżej przedstawiono inny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.

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

Dwa pola całkowite `i1` i `i2`, współużytkują te `lg`same lokalizacje pamięci co . Ten rodzaj kontroli nad układem struktury jest przydatne podczas korzystania z wywołania platformy.

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania języka C#](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (C#)](../reflection.md)
- [Atrybuty (C#)](index.md)
- [Tworzenie atrybutów niestandardowych (C#)](creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)](accessing-attributes-by-using-reflection.md)
