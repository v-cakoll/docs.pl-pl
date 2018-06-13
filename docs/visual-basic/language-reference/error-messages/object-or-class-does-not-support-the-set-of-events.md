---
title: Obiekt lub klasa nie obsługuje zbioru zdarzeń
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 4a6f1f59f43cdb351d49fbcbfd18362db888586e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593207"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="aee08-102">Obiekt lub klasa nie obsługuje zbioru zdarzeń</span><span class="sxs-lookup"><span data-stu-id="aee08-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="aee08-103">Próbowano użyć `WithEvents` zmiennej ze składnikiem, który nie może działać jako źródła zdarzeń dla określonego zestawu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aee08-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="aee08-104">Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt.</span><span class="sxs-lookup"><span data-stu-id="aee08-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="aee08-105">Mimo że może uważasz, że można obiekt sink zdarzenia z zaimplementowanym obiektu, to nie zawsze jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="aee08-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="aee08-106">`Implements` tylko implementuje interfejs dla metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="aee08-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="aee08-107">`WithEvents` nie jest obsługiwana w prywatnej `UserControls`, ponieważ informacje o typach wymagane do podnieść `ObjectEvent` nie jest dostępny w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aee08-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aee08-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="aee08-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="aee08-109">Nie można przechwytywać zdarzenia składnika, który nie źródła zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="aee08-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aee08-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aee08-110">See Also</span></span>  
 [<span data-ttu-id="aee08-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="aee08-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="aee08-112">Implements, instrukcja</span><span class="sxs-lookup"><span data-stu-id="aee08-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
