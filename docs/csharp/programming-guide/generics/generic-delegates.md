---
title: Delegaty ogólne C# — Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: 4e57256328fc81a485670b47fcf8fd1c38e26fac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712224"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="f9e13-102">Delegaty ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f9e13-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="f9e13-103">[Delegat](../../language-reference/builtin-types/reference-types.md) może definiować własne parametry typu.</span><span class="sxs-lookup"><span data-stu-id="f9e13-103">A [delegate](../../language-reference/builtin-types/reference-types.md) can define its own type parameters.</span></span> <span data-ttu-id="f9e13-104">Kod, który odwołuje się do delegata generycznego, może określić argument typu, aby utworzyć zamknięty typ skonstruowany, podobnie jak podczas tworzenia wystąpienia klasy generycznej lub wywołania metody ogólnej, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f9e13-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#36)]  
  
 <span data-ttu-id="f9e13-105">C#Wersja 2,0 ma nową funkcję, nazywana konwersją grupy metod, która ma zastosowanie do betonu i rodzajowych typów delegatów oraz pozwala napisać poprzedni wiersz z tą uproszczoną składnią:</span><span class="sxs-lookup"><span data-stu-id="f9e13-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#37)]  
  
 <span data-ttu-id="f9e13-106">Delegaty zdefiniowane w klasie generycznej mogą używać parametrów typu klasy generycznej w taki sam sposób, jak metody klasy.</span><span class="sxs-lookup"><span data-stu-id="f9e13-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#38)]  
  
 <span data-ttu-id="f9e13-107">Kod odwołujący się do delegata musi określać argument typu klasy zawierającej w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9e13-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#39)]  
  
 <span data-ttu-id="f9e13-108">Delegaty ogólne są szczególnie przydatne w definiowaniu zdarzeń na podstawie typowego wzorca projektowego, ponieważ argument nadawcy może być silnie określony i nie musi być już rzutowany do i z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="f9e13-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#40)]  
  
## <a name="see-also"></a><span data-ttu-id="f9e13-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9e13-109">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="f9e13-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f9e13-110">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f9e13-111">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="f9e13-111">Introduction to Generics</span></span>](./index.md)
- [<span data-ttu-id="f9e13-112">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e13-112">Generic Methods</span></span>](./generic-methods.md)
- [<span data-ttu-id="f9e13-113">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e13-113">Generic Classes</span></span>](./generic-classes.md)
- [<span data-ttu-id="f9e13-114">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e13-114">Generic Interfaces</span></span>](./generic-interfaces.md)
- [<span data-ttu-id="f9e13-115">Delegaci</span><span class="sxs-lookup"><span data-stu-id="f9e13-115">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="f9e13-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="f9e13-116">Generics</span></span>](../../../standard/generics/index.md)
