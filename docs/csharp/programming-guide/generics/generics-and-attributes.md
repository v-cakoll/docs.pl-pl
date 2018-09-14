---
title: Typy ogólne i atrybuty (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 0fe2d61001584aa7c175500bfa754b2ae2244660
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45560428"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="9633d-102">Typy ogólne i atrybuty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9633d-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="9633d-103">Można można zastosować atrybutów do typów ogólnych w taki sam sposób jak typów innych niż ogólne.</span><span class="sxs-lookup"><span data-stu-id="9633d-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="9633d-104">Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [atrybuty](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="9633d-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="9633d-105">Atrybuty niestandardowe są dozwolone tylko k odkazu otwartych typów ogólnych, które są typy rodzajowe, dla którego nie podano argumentów i zamkniętych skonstruowany typów ogólnych, które dostarczają argumenty dla wszystkich parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="9633d-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="9633d-106">W poniższych przykładach używane jest to atrybut niestandardowy:</span><span class="sxs-lookup"><span data-stu-id="9633d-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="9633d-107">To otwarty typ ogólny może odwoływać się do atrybutu:</span><span class="sxs-lookup"><span data-stu-id="9633d-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="9633d-108">Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9633d-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="9633d-109">W tym przykładzie `GenericClass2` ma dwa parametry typu:</span><span class="sxs-lookup"><span data-stu-id="9633d-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="9633d-110">Atrybut można odwołać się do zamkniętego skonstruowany typ rodzajowy:</span><span class="sxs-lookup"><span data-stu-id="9633d-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="9633d-111">Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="9633d-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="9633d-112">Typ ogólny nie może dziedziczyć z <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="9633d-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="9633d-113">Aby uzyskać informacje dotyczące typu ogólnego lub parametr typu w czasie wykonywania, można użyć metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="9633d-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="9633d-114">Aby uzyskać więcej informacji, zobacz [typy ogólne i odbicie](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="9633d-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9633d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9633d-115">See Also</span></span>

- [<span data-ttu-id="9633d-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9633d-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9633d-117">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="9633d-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
- [<span data-ttu-id="9633d-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9633d-118">Attributes</span></span>](../../../../docs/standard/attributes/index.md)
