---
title: Typy ogólne i atrybuty — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 99a24a7069145dfad5ce6c9c91f2a8653eb9a224
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589642"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="5ee91-102">Typy ogólne i atrybuty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5ee91-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="5ee91-103">Atrybuty mogą być stosowane do typów ogólnych w taki sam sposób jak typy nieogólne.</span><span class="sxs-lookup"><span data-stu-id="5ee91-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="5ee91-104">Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [atrybuty](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="5ee91-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="5ee91-105">Atrybuty niestandardowe są dozwolone tylko w celu odwoływania się do otwartych typów ogólnych, które są typami ogólnymi, dla których nie są dostarczane żadne argumenty typu, i zamknięto skonstruowane typy ogólne, które dostarczają argumentów dla wszystkich parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="5ee91-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="5ee91-106">W poniższych przykładach użyto tego atrybutu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="5ee91-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="5ee91-107">Atrybut może odwoływać się do otwartego typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="5ee91-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="5ee91-108">Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinków.</span><span class="sxs-lookup"><span data-stu-id="5ee91-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="5ee91-109">W tym przykładzie `GenericClass2` ma dwa parametry typu:</span><span class="sxs-lookup"><span data-stu-id="5ee91-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="5ee91-110">Atrybut może odwoływać się do zamkniętego skonstruowanego typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="5ee91-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="5ee91-111">Atrybut, który odwołuje się do parametru typu ogólnego, spowoduje błąd czasu kompilacji:</span><span class="sxs-lookup"><span data-stu-id="5ee91-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="5ee91-112">Typ ogólny nie może dziedziczyć <xref:System.Attribute>po elemencie:</span><span class="sxs-lookup"><span data-stu-id="5ee91-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="5ee91-113">Aby uzyskać informacje o typie ogólnym lub parametrze typu w czasie wykonywania, można użyć metod <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="5ee91-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="5ee91-114">Aby uzyskać więcej informacji, zobacz [Ogólne i odbicie](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="5ee91-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee91-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ee91-115">See also</span></span>

- [<span data-ttu-id="5ee91-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5ee91-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5ee91-117">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5ee91-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="5ee91-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5ee91-118">Attributes</span></span>](../../../standard/attributes/index.md)
