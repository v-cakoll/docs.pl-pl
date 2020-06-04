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
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="c59bd-102">Instrukcje: tworzenie Unii C/C++ za pomocą atrybutów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c59bd-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="c59bd-103">Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c59bd-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="c59bd-104">Na przykład, można utworzyć elementy znane jako Unia w C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` `FieldOffset` atrybutów i.</span><span class="sxs-lookup"><span data-stu-id="c59bd-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="c59bd-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c59bd-105">Example</span></span>

<span data-ttu-id="c59bd-106">W tym segmencie kodu wszystkie pola, które są `TestUnion` uruchamiane w tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c59bd-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

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

## <a name="example"></a><span data-ttu-id="c59bd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c59bd-107">Example</span></span>

<span data-ttu-id="c59bd-108">Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="c59bd-108">The following is another example where fields start at different explicitly set locations.</span></span>

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

<span data-ttu-id="c59bd-109">Dwa pola liczb całkowitych `i1` i `i2` , współużytkują te same lokalizacje pamięci co `lg` .</span><span class="sxs-lookup"><span data-stu-id="c59bd-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="c59bd-110">Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="c59bd-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="c59bd-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c59bd-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="c59bd-112">Przewodnik programowania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c59bd-112">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="c59bd-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c59bd-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="c59bd-114">Odbicie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c59bd-114">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="c59bd-115">Atrybuty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c59bd-115">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="c59bd-116">Tworzenie atrybutów niestandardowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c59bd-116">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="c59bd-117">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c59bd-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
