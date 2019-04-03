---
title: Zdarzenie „<eventname1>” nie może implementować zdarzenia „<eventname2>” w interfejsie „<interface>”, ponieważ ich typy delegowane „<delegate1>” i „<delegate2>” są niezgodne
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 9581168fa86f8f0715e004b60c2eb2a813cd38ab
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840526"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="299fa-102">Zdarzenie "\<eventname1 >' nie może implementować zdarzenia"\<eventname2 > "w interfejsie"\<interfejsu > "ponieważ ich typy delegowane\<delegate1 >" i "\<delegate2 >' nie są zgodne</span><span class="sxs-lookup"><span data-stu-id="299fa-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="299fa-103">Visual Basic nie może implementować zdarzenia, ponieważ typ delegata zdarzenia jest niezgodny z typem delegata, zdarzenia w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="299fa-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="299fa-104">Ten błąd może wystąpić, gdy można zdefiniować wiele zdarzeń w interfejsie, a następnie spróbuj ich implementacji wraz z tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="299fa-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="299fa-105">Zdarzenie można zaimplementować dwa lub więcej zdarzeń tylko wtedy, gdy wszystko jest implementowane zdarzenia są deklarowane przy użyciu `As` składni i określić ten sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="299fa-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="299fa-106">**Identyfikator błędu:** BC31423</span><span class="sxs-lookup"><span data-stu-id="299fa-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="299fa-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="299fa-107">To correct this error</span></span>  
  
-   <span data-ttu-id="299fa-108">Zdarzenia należy wdrożyć osobno.</span><span class="sxs-lookup"><span data-stu-id="299fa-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="299fa-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="299fa-109">—or—</span></span>  
  
-   <span data-ttu-id="299fa-110">Definiowanie zdarzenia przy użyciu interfejsu `As` składni i określić ten sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="299fa-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="299fa-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="299fa-111">See also</span></span>

- [<span data-ttu-id="299fa-112">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="299fa-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="299fa-113">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="299fa-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="299fa-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="299fa-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
