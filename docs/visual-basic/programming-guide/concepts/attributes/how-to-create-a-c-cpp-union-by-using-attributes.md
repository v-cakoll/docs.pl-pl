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
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="3e577-102">Instrukcje: Tworzenie elementu C/C++ Union przy użyciu atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e577-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="3e577-103">Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3e577-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="3e577-104">Na przykład można utworzyć element, który jest znany jako Unia w C/C++ przy użyciu atrybutów `StructLayout(LayoutKind.Explicit)` i `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="3e577-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="3e577-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e577-105">Example</span></span>

<span data-ttu-id="3e577-106">W tym segmencie kodu wszystkie pola `TestUnion` są uruchamiane w tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="3e577-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="3e577-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e577-107">Example</span></span>

<span data-ttu-id="3e577-108">Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3e577-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="3e577-109">Pola dwóch liczb całkowitych, `i1` i `i2`, współużytkują te same lokalizacje pamięci co `lg`.</span><span class="sxs-lookup"><span data-stu-id="3e577-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="3e577-110">Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="3e577-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="3e577-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e577-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="3e577-112">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e577-112">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="3e577-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e577-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="3e577-114">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e577-114">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="3e577-115">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e577-115">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="3e577-116">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e577-116">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="3e577-117">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e577-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
