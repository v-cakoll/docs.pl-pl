---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778641"
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="967de-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="967de-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="967de-103">Określa, że co najmniej jednej zmiennej zadeklarowanej składowej odnoszą się do wystąpienia klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="967de-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="967de-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="967de-104">Remarks</span></span>  
 <span data-ttu-id="967de-105">Gdy zmienna jest zdefiniowana za pomocą `WithEvents`, deklaratywne określenie, zmiennej na zdarzenia przy użyciu obsługiwała `Handles` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="967de-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="967de-106">Możesz użyć `WithEvents` tylko na poziomie klasy lub modułu.</span><span class="sxs-lookup"><span data-stu-id="967de-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="967de-107">Oznacza to, że kontekst deklaracji `WithEvents` zmienna musi być klasą lub moduł i nie może być plikiem źródłowym, przestrzeni nazw, struktura lub procedury.</span><span class="sxs-lookup"><span data-stu-id="967de-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="967de-108">Nie można użyć `WithEvents` członka struktury.</span><span class="sxs-lookup"><span data-stu-id="967de-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="967de-109">Można zadeklarować tylko zmienne poszczególnych — tablice nie — z `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="967de-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="967de-110">reguły</span><span class="sxs-lookup"><span data-stu-id="967de-110">Rules</span></span>  
  
- <span data-ttu-id="967de-111">**Typy elementów.**</span><span class="sxs-lookup"><span data-stu-id="967de-111">**Element Types.**</span></span> <span data-ttu-id="967de-112">Musisz zadeklarować `WithEvents` zmienne jako zmienne do obiektu, dzięki czemu mogą akceptować klasy wystąpień.</span><span class="sxs-lookup"><span data-stu-id="967de-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="967de-113">Jednak nie można zadeklarować je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="967de-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="967de-114">Musisz je zadeklarować jako określonej klasy, które może wywoływać zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="967de-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="967de-115">`WithEvents` Modyfikatora można używać w tym kontekście: [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="967de-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967de-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="967de-116">See also</span></span>

- [<span data-ttu-id="967de-117">Handles</span><span class="sxs-lookup"><span data-stu-id="967de-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="967de-118">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="967de-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="967de-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="967de-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
