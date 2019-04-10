---
title: Obiekt lub klasa nie obsługuje zbioru zdarzeń
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59342885"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="8f3b2-102">Obiekt lub klasa nie obsługuje zbioru zdarzeń</span><span class="sxs-lookup"><span data-stu-id="8f3b2-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="8f3b2-103">Próbowano użyć `WithEvents` zmiennej za pomocą składnika, który nie może działać jako źródło zdarzeń dla określonego zestawu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="8f3b2-104">Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="8f3b2-105">Mimo że myślisz, że można przechwytywać zdarzenia z zaimplementowaną obiektu, nie zawsze jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> `Implements` <span data-ttu-id="8f3b2-106">tylko implementuje interfejs dla metod i właściwości.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-106">only implements an interface for methods and properties.</span></span> `WithEvents` <span data-ttu-id="8f3b2-107">nie jest obsługiwana dla prywatnych `UserControls`, ponieważ wymagane informacje dotyczące typu podnieść `ObjectEvent` nie jest dostępna w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-107">is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f3b2-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="8f3b2-108">To correct this error</span></span>  
  
1. <span data-ttu-id="8f3b2-109">Nie można wychwytywanie zdarzeń interfejsu składnika, który nie źródeł zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8f3b2-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f3b2-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f3b2-110">See also</span></span>

- [<span data-ttu-id="8f3b2-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="8f3b2-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="8f3b2-112">Implements — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="8f3b2-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
