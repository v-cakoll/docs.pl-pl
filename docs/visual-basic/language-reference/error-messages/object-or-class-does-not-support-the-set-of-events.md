---
title: "Obiekt lub klasa nie obsługuje zbioru zdarzeń"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="491fc-102">Obiekt lub klasa nie obsługuje zbioru zdarzeń</span><span class="sxs-lookup"><span data-stu-id="491fc-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="491fc-103">Próbowano użyć `WithEvents` zmiennej ze składnikiem, który nie może działać jako źródła zdarzeń dla określonego zestawu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="491fc-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="491fc-104">Na przykład chcesz przechwytywać zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` pierwszy obiekt.</span><span class="sxs-lookup"><span data-stu-id="491fc-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="491fc-105">Mimo że może uważasz, że można obiekt sink zdarzenia z zaimplementowanym obiektu, to nie zawsze jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="491fc-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="491fc-106">`Implements`tylko implementuje interfejs dla metody i właściwości.</span><span class="sxs-lookup"><span data-stu-id="491fc-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="491fc-107">`WithEvents`nie jest obsługiwana w prywatnej `UserControls`, ponieważ informacje o typach wymagane do podnieść `ObjectEvent` nie jest dostępny w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="491fc-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="491fc-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="491fc-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="491fc-109">Nie można przechwytywać zdarzenia składnika, który nie źródła zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="491fc-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="491fc-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="491fc-110">See Also</span></span>  
 [<span data-ttu-id="491fc-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="491fc-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="491fc-112">Implements — instrukcja</span><span class="sxs-lookup"><span data-stu-id="491fc-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
