---
title: Delegaty ogólne (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], delegates
- delegates [C#], generic
ms.assetid: bdea509c-44c1-4309-aaa9-15c7aee009df
ms.openlocfilehash: a9f06dcf608a83b53e894310f20810182cf6daa4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332910"
---
# <a name="generic-delegates-c-programming-guide"></a><span data-ttu-id="135d8-102">Delegaty ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="135d8-102">Generic Delegates (C# Programming Guide)</span></span>
<span data-ttu-id="135d8-103">A [delegować](../../../csharp/language-reference/keywords/delegate.md) można zdefiniować własny parametrów typu.</span><span class="sxs-lookup"><span data-stu-id="135d8-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can define its own type parameters.</span></span> <span data-ttu-id="135d8-104">Kod, że odwołania Delegat ogólny można określić argumentu typu można utworzyć typu skonstruowane zamknięte, podobnie jak w przypadku tworzenia wystąpienia klasy ogólnej lub wywołanie metody ogólnej, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="135d8-104">Code that references the generic delegate can specify the type argument to create a closed constructed type, just like when instantiating a generic class or calling a generic method, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#36](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_1.cs)]  
  
 <span data-ttu-id="135d8-105">C# w wersji 2.0 zawiera nową funkcję o nazwie konwersji grupy — metoda, która stosuje się do typów delegatów konkretnych, jak również ogólne i umożliwia pisanie poprzedniego wiersza przy użyciu tej składni uproszczoną:</span><span class="sxs-lookup"><span data-stu-id="135d8-105">C# version 2.0 has a new feature called method group conversion, which applies to concrete as well as generic delegate types, and enables you to write the previous line with this simplified syntax:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#37](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_2.cs)]  
  
 <span data-ttu-id="135d8-106">Delegaty zdefiniowany w klasie ogólnej można używać parametrów typu klasy ogólnej w taki sam sposób, że metody klasy.</span><span class="sxs-lookup"><span data-stu-id="135d8-106">Delegates defined within a generic class can use the generic class type parameters in the same way that class methods do.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#38](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_3.cs)]  
  
 <span data-ttu-id="135d8-107">Kod, który odwołuje się do delegata należy określić argument typu zawierającego klasy, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="135d8-107">Code that references the delegate must specify the type argument of the containing class, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#39](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_4.cs)]  
  
 <span data-ttu-id="135d8-108">Delegaty ogólne są szczególnie przydatne podczas definiowania zdarzenia oparte na wzorcu typowe, ponieważ argumentu sender mogą być silnie typizowane i nie ma już można rzutować do i z <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="135d8-108">Generic delegates are especially useful in defining events based on the typical design pattern because the sender argument can be strongly typed and no longer has to be cast to and from <xref:System.Object>.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#40](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-delegates_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="135d8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="135d8-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="135d8-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="135d8-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="135d8-111">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="135d8-111">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="135d8-112">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="135d8-112">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
 [<span data-ttu-id="135d8-113">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="135d8-113">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
 [<span data-ttu-id="135d8-114">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="135d8-114">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
 [<span data-ttu-id="135d8-115">Delegaci</span><span class="sxs-lookup"><span data-stu-id="135d8-115">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="135d8-116">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="135d8-116">Generics</span></span>](~/docs/standard/generics/index.md)
