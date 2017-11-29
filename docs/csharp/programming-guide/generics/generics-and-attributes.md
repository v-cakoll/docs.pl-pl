---
title: "Typy ogólne i atrybuty (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5535334514afb0b9891dfce2e0cc0a0e95526069
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="f4a1f-102">Typy ogólne i atrybuty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f4a1f-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="f4a1f-103">Atrybuty może odnosić się do typów ogólnych w taki sam sposób jak typy nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="f4a1f-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="f4a1f-104">Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [atrybutów](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="f4a1f-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="f4a1f-105">Atrybuty niestandardowe są dozwolone tylko do odwołania Otwórz typów ogólnych, które są typów ogólnych, dla jakiego typu nie podano argumentów i zamknięte skonstruowane typów ogólnych, które dostarczają argumenty dla wszystkich parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="f4a1f-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="f4a1f-106">W poniższych przykładach użyto tego atrybutu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 <span data-ttu-id="f4a1f-107">Atrybut może odwoływać się otwartym typem ogólnym:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 <span data-ttu-id="f4a1f-108">Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinkami.</span><span class="sxs-lookup"><span data-stu-id="f4a1f-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="f4a1f-109">W tym przykładzie `GenericClass2` zawiera dwa parametry typu:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 <span data-ttu-id="f4a1f-110">Atrybut może odwoływać się zamkniętego skonstruowanego typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 <span data-ttu-id="f4a1f-111">Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 <span data-ttu-id="f4a1f-112">Nie może dziedziczyć po typie ogólnym <xref:System.Attribute>:</span><span class="sxs-lookup"><span data-stu-id="f4a1f-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 <span data-ttu-id="f4a1f-113">Aby uzyskać informacje o typie ogólnym lub parametru typu w czasie wykonywania, można użyć metody <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="f4a1f-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="f4a1f-114">Aby uzyskać więcej informacji, zobacz [typy ogólne i odbicie](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="f4a1f-114">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4a1f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4a1f-115">See Also</span></span>  
 [<span data-ttu-id="f4a1f-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f4a1f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f4a1f-117">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f4a1f-117">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="f4a1f-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f4a1f-118">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)
