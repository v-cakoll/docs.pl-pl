---
title: 'Porady: tworzenie Unii C-C++ za pomocą atrybutów (C#)'
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 8b5a88656b1172407c3e5b9f5198d5acae7bf9e0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558008"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="6ee44-102">Porady: tworzenie złożenia C/C++ za pomocą atrybutów (C#)</span><span class="sxs-lookup"><span data-stu-id="6ee44-102">How to: Create a C/C++ Union by Using Attributes (C#)</span></span>
<span data-ttu-id="6ee44-103">Za pomocą atrybutów można dostosować, jak struktury są ułożone w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ee44-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="6ee44-104">Na przykład można utworzyć, co jest nazywane Unia w języku C/C++ za pomocą `StructLayout(LayoutKind.Explicit)` i `FieldOffset` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="6ee44-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee44-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ee44-105">Example</span></span>  
 <span data-ttu-id="6ee44-106">W tym segmencie kodu, wszystkie pola z `TestUnion` rozpoczynają się od tej samej lokalizacji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="6ee44-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6ee44-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ee44-107">Example</span></span>  
 <span data-ttu-id="6ee44-108">Oto inny przykład gdzie pola zaczynają się w różnych jawnie ustawić lokalizacje.</span><span class="sxs-lookup"><span data-stu-id="6ee44-108">The following is another example where fields start at different explicitly set locations.</span></span>  
  
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
  
 <span data-ttu-id="6ee44-109">Pola dwóch liczb całkowitych, `i1` i `i2`, Udostępnij te same lokalizacje pamięci jako `lg`.</span><span class="sxs-lookup"><span data-stu-id="6ee44-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="6ee44-110">Tego rodzaju kontrolę nad układzie struktury jest przydatne, gdy za pomocą wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="6ee44-110">This sort of control over struct layout is useful when using platform invocation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ee44-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ee44-111">See Also</span></span>

- <xref:System.Reflection>  
- <xref:System.Attribute>  
- [<span data-ttu-id="6ee44-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6ee44-112">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6ee44-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6ee44-113">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)  
- [<span data-ttu-id="6ee44-114">Odbicie (C#)</span><span class="sxs-lookup"><span data-stu-id="6ee44-114">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
- [<span data-ttu-id="6ee44-115">Atrybuty (C#)</span><span class="sxs-lookup"><span data-stu-id="6ee44-115">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="6ee44-116">Tworzenie atrybutów niestandardowych (C#)</span><span class="sxs-lookup"><span data-stu-id="6ee44-116">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
- [<span data-ttu-id="6ee44-117">Uzyskiwanie dostępu do atrybutów przy użyciu odbicia (C#)</span><span class="sxs-lookup"><span data-stu-id="6ee44-117">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
