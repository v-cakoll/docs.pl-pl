---
title: "Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords: BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="cd275-102">Zdarzenia zmiennych WithEvents nie mogą być obsługiwane przez metody nieudostępnione</span><span class="sxs-lookup"><span data-stu-id="cd275-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="cd275-103">Zmienna zadeklarowana ze `Shared` modyfikator jest udostępniona zmienna.</span><span class="sxs-lookup"><span data-stu-id="cd275-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="cd275-104">Udostępniona zmienna identyfikuje dokładnie jedną lokalizację magazynu.</span><span class="sxs-lookup"><span data-stu-id="cd275-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="cd275-105">Zmienna zadeklarowana ze `WithEvents` modyfikator potwierdza, że typ, do której należy zmienna obsługuje zbioru zdarzeń zgłasza zmiennej.</span><span class="sxs-lookup"><span data-stu-id="cd275-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="cd275-106">Gdy wartość jest przypisany do zmiennej, właściwość utworzone przez `WithEvents` deklaracji unhooks dowolnego istniejącego programu obsługi zdarzeń i przechwytuje się nowy program obsługi zdarzeń za pomocą `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="cd275-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="cd275-107">**Identyfikator błędu:** BC30594</span><span class="sxs-lookup"><span data-stu-id="cd275-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd275-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="cd275-108">To correct this error</span></span>  
  
-   <span data-ttu-id="cd275-109">Zadeklaruj procedury obsługi zdarzenia `Shared`.</span><span class="sxs-lookup"><span data-stu-id="cd275-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd275-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd275-110">See Also</span></span>  
 [<span data-ttu-id="cd275-111">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="cd275-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="cd275-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="cd275-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
