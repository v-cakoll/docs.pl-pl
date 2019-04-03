---
title: 'Instrukcje: Tworzenie Unii C-C++ za pomocą atrybutów (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 0c3ebf248f5d2f20e2fff25fb8326a294b51d153
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829307"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a>Instrukcje: Tworzenie złożenia C/C++ za pomocą atrybutów (Visual Basic)
Za pomocą atrybutów można dostosować, jak struktury są ułożone w pamięci. Na przykład można utworzyć, co jest nazywane Unia w języku C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` i `FieldOffset` atrybutów.  
  
## <a name="example"></a>Przykład  
 W tym segmencie kodu, wszystkie pola z `TestUnion` rozpoczynają się od tej samej lokalizacji w pamięci.  
  
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
 Oto inny przykład gdzie pola zaczynają się w różnych jawnie ustawić lokalizacje.  
  
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
  
 Pola dwóch liczb całkowitych, `i1` i `i2`, Udostępnij te same lokalizacje pamięci jako `lg`. Tego rodzaju kontrolę nad układzie struktury jest przydatne, gdy za pomocą wywołania platformy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Reflection>
- <xref:System.Attribute>
- [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)
- [Atrybuty](../../../../standard/attributes/index.md)
- [Odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Atrybuty (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Tworzenie atrybutów niestandardowych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
