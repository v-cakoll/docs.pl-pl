---
title: Delegaty ogólne C# — Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 31ab511bf88bfbc2134029564ecbf70aa75119d7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659850"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="6a4b6-102">Delegaty ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6a4b6-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="6a4b6-103">[Delegat](../../language-reference/keywords/delegate.md) może definiować własne parametry typu.</span><span class="sxs-lookup"><span data-stu-id="6a4b6-103">A [delegate](../../language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="6a4b6-104">Kod, który odwołuje się do delegata generycznego, może określić argument typu, aby utworzyć zamknięty typ skonstruowany, podobnie jak podczas tworzenia wystąpienia klasy generycznej lub wywołania metody ogólnej, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6a4b6-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="6a4b6-105">C#Wersja 2,0 ma nową funkcję, nazywana konwersją grupy metod, która ma zastosowanie do betonu i rodzajowych typów delegatów oraz pozwala napisać poprzedni wiersz z tą uproszczoną składnią:</span><span class="sxs-lookup"><span data-stu-id="6a4b6-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="6a4b6-106">Delegaty zdefiniowane w klasie generycznej mogą używać parametrów typu klasy generycznej w taki sam sposób, jak metody klasy.</span><span class="sxs-lookup"><span data-stu-id="6a4b6-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="6a4b6-107">Kod odwołujący się do delegata musi określać argument typu klasy zawierającej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6a4b6-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="6a4b6-108">Delegaty ogólne są szczególnie przydatne w definiowaniu zdarzeń na podstawie typowego wzorca projektowego, ponieważ argument nadawcy może być silnie określony i nie musi być już <xref:System.Object>rzutowany do i z.</span><span class="sxs-lookup"><span data-stu-id="6a4b6-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="6a4b6-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a4b6-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="6a4b6-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6a4b6-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6a4b6-111">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="6a4b6-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="6a4b6-112">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="6a4b6-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="6a4b6-113">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="6a4b6-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="6a4b6-114">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="6a4b6-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="6a4b6-115">Delegaty</span><span class="sxs-lookup"><span data-stu-id="6a4b6-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="6a4b6-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="6a4b6-116">Generics</span></span>](../../../standard/generics/index.md)
