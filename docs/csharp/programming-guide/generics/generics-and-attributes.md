---
title: Rodzajowe i atrybuty — przewodnik programowania języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703029"
---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="ba9dc-102">Typy ogólne i atrybuty (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ba9dc-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="ba9dc-103">Atrybuty mogą być stosowane do typów ogólnych w taki sam sposób jak typy nierodzajowe.</span><span class="sxs-lookup"><span data-stu-id="ba9dc-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="ba9dc-104">Aby uzyskać więcej informacji na temat stosowania atrybutów, zobacz [Atrybuty](../concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ba9dc-104">For more information on applying attributes, see [Attributes](../concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="ba9dc-105">Atrybuty niestandardowe są dozwolone tylko do odwoływania się do otwartych typów ogólnych, które są typami ogólnymi, dla których nie są dostarczane żadne argumenty typu, i zamknięte skonstruowane typy ogólne, które dostarczają argumenty dla wszystkich parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="ba9dc-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="ba9dc-106">W poniższych przykładach używa się tego atrybutu niestandardowego:</span><span class="sxs-lookup"><span data-stu-id="ba9dc-106">The following examples use this custom attribute:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 <span data-ttu-id="ba9dc-107">Atrybut może odwoływać się do otwartego typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="ba9dc-107">An attribute can reference an open generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 <span data-ttu-id="ba9dc-108">Określ wiele parametrów typu przy użyciu odpowiedniej liczby przecinków.</span><span class="sxs-lookup"><span data-stu-id="ba9dc-108">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="ba9dc-109">W tym `GenericClass2` przykładzie ma dwa parametry typu:</span><span class="sxs-lookup"><span data-stu-id="ba9dc-109">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 <span data-ttu-id="ba9dc-110">Atrybut może odwoływać się do zamkniętego skonstruowanego typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="ba9dc-110">An attribute can reference a closed constructed generic type:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 <span data-ttu-id="ba9dc-111">Atrybut, który odwołuje się do parametru typu ogólnego spowoduje błąd w czasie kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ba9dc-111">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 <span data-ttu-id="ba9dc-112">Typ ogólny nie <xref:System.Attribute>może dziedziczyć z :</span><span class="sxs-lookup"><span data-stu-id="ba9dc-112">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 <span data-ttu-id="ba9dc-113">Aby uzyskać informacje o typie ogólnym lub parametrze typu w <xref:System.Reflection>czasie wykonywania, można użyć metod .</span><span class="sxs-lookup"><span data-stu-id="ba9dc-113">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="ba9dc-114">Aby uzyskać więcej informacji, zobacz [Generyki i Refleksje](./generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="ba9dc-114">For more information, see [Generics and Reflection](./generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba9dc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba9dc-115">See also</span></span>

- [<span data-ttu-id="ba9dc-116">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ba9dc-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ba9dc-117">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="ba9dc-117">Generics</span></span>](./index.md)
- [<span data-ttu-id="ba9dc-118">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ba9dc-118">Attributes</span></span>](../../../standard/attributes/index.md)
