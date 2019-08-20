---
title: 'Instrukcje: UtwórzC++ Unię C przy użyciu atrybutów (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: fdadc9505b93f40c66001ac36345efada2edd270
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595374"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="e77de-102">Instrukcje: Utwórz element C/C++ Union przy użyciu atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="e77de-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="e77de-103">Przy użyciu atrybutów można dostosować sposób, w jaki struktury są ułożone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e77de-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="e77de-104">Na przykład można utworzyć element, który jest znany jako Unia w C/C++ przy użyciu `StructLayout(LayoutKind.Explicit)` atrybutów i. `FieldOffset`</span><span class="sxs-lookup"><span data-stu-id="e77de-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e77de-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e77de-105">Example</span></span>  
 <span data-ttu-id="e77de-106">W tym segmencie kodu wszystkie pola, które `TestUnion` są uruchamiane w tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e77de-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="e77de-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="e77de-107">Example</span></span>  
 <span data-ttu-id="e77de-108">Poniżej znajduje się kolejny przykład, w którym pola zaczynają się od różnych jawnie ustawionych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="e77de-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="e77de-109">Dwa pola `i1` liczb całkowitych i `i2`, współużytkują te same lokalizacje `lg`pamięci co.</span><span class="sxs-lookup"><span data-stu-id="e77de-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="e77de-110">Ten rodzaj kontroli nad układem struktury jest przydatny podczas korzystania z wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="e77de-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77de-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e77de-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e77de-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e77de-112">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="e77de-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e77de-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="e77de-114">OdbicieC#()</span><span class="sxs-lookup"><span data-stu-id="e77de-114">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="e77de-115">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="e77de-115">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="e77de-116">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="e77de-116">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
- [<span data-ttu-id="e77de-117">Uzyskiwanie dostępu do atrybutów przyC#użyciu odbicia ()</span><span class="sxs-lookup"><span data-stu-id="e77de-117">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
