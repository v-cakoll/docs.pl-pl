---
title: Delegaty ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: ff19b3d71858552158a8ae5d0ab362a86dc98e65
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423495"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="0e8b3-102">Delegaty ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0e8b3-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="0e8b3-103">A [delegować](../../../csharp/language-reference/keywords/delegate.md) można zdefiniować własne parametry typu.</span><span class="sxs-lookup"><span data-stu-id="0e8b3-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="0e8b3-104">Kod, że odwołania Delegat ogólny można określić argument typu w celu utworzenia zamknięte skonstruowanego typu, podobnie jak podczas tworzenia wystąpienia klasy ogólnej lub wywoływania metody rodzajowej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0e8b3-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="0e8b3-105">C# w wersji 2.0 zawiera nową funkcję o nazwie metody konwersji grupy dotyczy typów konkretnych, jak również ogólne delegata, która umożliwia pisanie poprzedniego wiersza składnią uproszczoną:</span><span class="sxs-lookup"><span data-stu-id="0e8b3-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="0e8b3-106">Delegaty zdefiniowany w ramach klasy ogólnej można użyć parametrów typu rodzajowego klasy w taki sam sposób, który do metody klasy.</span><span class="sxs-lookup"><span data-stu-id="0e8b3-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="0e8b3-107">Kod, który odwołuje się do obiektu delegowanego należy określić argument typu zawierającego klasy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0e8b3-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="0e8b3-108">Delegaty ogólne są szczególnie użyteczne w definiując zdarzenia, oparta na wzorcu projektów, ponieważ argument nadawca może być silnie typizowane i nie ma już można rzutować do i z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0e8b3-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="0e8b3-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0e8b3-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="0e8b3-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0e8b3-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0e8b3-111">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="0e8b3-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/index.md)
- [<span data-ttu-id="0e8b3-112">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="0e8b3-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)
- [<span data-ttu-id="0e8b3-113">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="0e8b3-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)
- [<span data-ttu-id="0e8b3-114">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="0e8b3-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)
- [<span data-ttu-id="0e8b3-115">Delegaty</span><span class="sxs-lookup"><span data-stu-id="0e8b3-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="0e8b3-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="0e8b3-116">Generics</span></span>](~/docs/standard/generics/index.md)
