---
title: Delegaci ogólny — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712224"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="af394-102">Delegaty ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="af394-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="af394-103">[Pełnomocnik](../../language-reference/builtin-types/reference-types.md) może zdefiniować własne parametry typu.</span><span class="sxs-lookup"><span data-stu-id="af394-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="af394-104">Kod, który odwołuje się do delegata ogólnego można określić argument typu, aby utworzyć zamknięty typ konstruowany, podobnie jak podczas tworzenia wystąpienia klasy ogólnej lub wywoływania metody ogólnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="af394-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="af394-105">C# w wersji 2.0 ma nową funkcję o nazwie konwersja grupy metod, która ma zastosowanie do konkretnych, jak i ogólnych typów delegatów i umożliwia zapisanie poprzedniego wiersza z tej uproszczonej składni:</span><span class="sxs-lookup"><span data-stu-id="af394-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="af394-106">Delegaci zdefiniowane w klasie ogólnej można użyć parametrów typu klasy ogólnej w taki sam sposób, jak metody klasy zrobić.</span><span class="sxs-lookup"><span data-stu-id="af394-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="af394-107">Kod, który odwołuje się do delegata musi określać argument typu zawierającej klasę, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="af394-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="af394-108">Delegaci rodzajowy są szczególnie przydatne w definiowaniu zdarzeń na podstawie typowego wzorca projektu, ponieważ argument nadawcy może być silnie wpisany i nie musi być już rzutowane do iz <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="af394-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="af394-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af394-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="af394-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="af394-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="af394-111">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="af394-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="af394-112">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="af394-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="af394-113">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="af394-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="af394-114">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="af394-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="af394-115">Delegaty</span><span class="sxs-lookup"><span data-stu-id="af394-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="af394-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="af394-116">Generics</span></span>](../../../standard/generics/index.md)
