---
title: 'Instrukcje: tworzenie Unii C-C + + przy użyciu atrybutów'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400684"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Instrukcje: tworzenie Unii C/C++ za pomocą atrybutów (Visual Basic)

Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci. Na przykład, można utworzyć elementy znane jako Unia w C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` `FieldOffset` atrybutów i.

## <a name="example"></a>Przykład

W tym segmencie kodu wszystkie pola, które są `TestUnion` uruchamiane w tej samej lokalizacji w pamięci.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a>Przykład

Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

Dwa pola liczb całkowitych `i1` i `i2` , współużytkują te same lokalizacje pamięci co `lg` . Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.

## <a name="see-also"></a>Zobacz też

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w Visual Basic](../../index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../reflection.md)
- [Atrybuty (Visual Basic)](../../../language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](accessing-attributes-by-using-reflection.md)
