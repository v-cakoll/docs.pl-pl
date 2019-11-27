---
title: 'Instrukcje: TworzenieC++ Unii C przy użyciu atrybutów'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: acb8dc781e2872ae46e5aa058a98b3dd98f3e064
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349497"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Instrukcje: Tworzenie elementu C/C++ Union przy użyciu atrybutów (Visual Basic)

Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci. Na przykład można utworzyć element, który jest znany jako Unia w C/C++ przy użyciu atrybutów `StructLayout(LayoutKind.Explicit)` i `FieldOffset`.

## <a name="example"></a>Przykład

W tym segmencie kodu wszystkie pola `TestUnion` są uruchamiane w tej samej lokalizacji w pamięci.

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

Pola dwóch liczb całkowitych, `i1` i `i2`, współużytkują te same lokalizacje pamięci co `lg`. Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.

## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
