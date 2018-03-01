---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="1d703-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d703-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="1d703-103">Określa, że co najmniej jeden zadeklarowana zmienna elementu członkowskiego odwołują się do wystąpienia klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d703-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d703-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d703-104">Remarks</span></span>  
 <span data-ttu-id="1d703-105">Jeśli zmienna jest zdefiniowana za pomocą `WithEvents`, deklaratywnego można określić zdarzenia zmiennej przy użyciu obsługiwała `Handles` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1d703-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="1d703-106">Można użyć `WithEvents` tylko na poziomie klasę lub moduł.</span><span class="sxs-lookup"><span data-stu-id="1d703-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="1d703-107">Oznacza to, że w kontekście deklaracji `WithEvents` zmiennej musi być klasą lub modułu i nie może być plik źródłowy, przestrzeni nazw, struktury lub procedury.</span><span class="sxs-lookup"><span data-stu-id="1d703-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="1d703-108">Nie można użyć `WithEvents` dla elementu członkowskiego struktury.</span><span class="sxs-lookup"><span data-stu-id="1d703-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="1d703-109">Można zadeklarować tylko pojedyncze zmienne — nie stałych — z `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="1d703-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="1d703-110">Reguły</span><span class="sxs-lookup"><span data-stu-id="1d703-110">Rules</span></span>  
  
-   <span data-ttu-id="1d703-111">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="1d703-111">**Element Types.**</span></span> <span data-ttu-id="1d703-112">Musisz zadeklarować `WithEvents` zmienne, które mają być obiekt zmienne, tak aby mogą akceptować klasy wystąpień.</span><span class="sxs-lookup"><span data-stu-id="1d703-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="1d703-113">Jednak nie można zadeklarować je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="1d703-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="1d703-114">Musisz zadeklarować je jako określonej klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1d703-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="1d703-115">`WithEvents` Modyfikatora można używać w tym kontekście: [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="1d703-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d703-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d703-116">See Also</span></span>  
 [<span data-ttu-id="1d703-117">Uchwyty</span><span class="sxs-lookup"><span data-stu-id="1d703-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="1d703-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1d703-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="1d703-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1d703-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
