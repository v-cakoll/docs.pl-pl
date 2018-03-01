---
title: "AddHandler — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="181d3-102">AddHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="181d3-102">AddHandler Statement</span></span>
<span data-ttu-id="181d3-103">Kojarzy zdarzenie z obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="181d3-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="181d3-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="181d3-105">Części</span><span class="sxs-lookup"><span data-stu-id="181d3-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="181d3-106">Nazwa zdarzenia do obsługi.</span><span class="sxs-lookup"><span data-stu-id="181d3-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="181d3-107">Nazwa procedury, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="181d3-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="181d3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="181d3-108">Remarks</span></span>  
 <span data-ttu-id="181d3-109">`AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w czasie wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="181d3-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="181d3-110">Podpis `eventhandler` procedury muszą być zgodne podpisu zdarzenia `event`.</span><span class="sxs-lookup"><span data-stu-id="181d3-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="181d3-111">`Handles` — Słowo kluczowe i `AddHandler` instrukcji zarówno umożliwiają określenie określone procedury obsługi zdarzeń w szczególności, że istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="181d3-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="181d3-112">`AddHandler` Instrukcji procedury łączy się z zdarzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="181d3-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="181d3-113">Użyj `Handles` — słowo kluczowe podczas definiowania procedury, aby określić, czy obsługuje ona określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="181d3-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="181d3-114">Aby uzyskać więcej informacji, zobacz [obsługuje](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="181d3-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="181d3-115">W przypadku niestandardowych zdarzeń `AddHandler` instrukcja wywołuje zdarzenie `AddHandler` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="181d3-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="181d3-116">Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="181d3-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="181d3-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="181d3-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="181d3-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="181d3-118">See Also</span></span>  
 [<span data-ttu-id="181d3-119">RemoveHandler — instrukcja</span><span class="sxs-lookup"><span data-stu-id="181d3-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="181d3-120">Uchwyty</span><span class="sxs-lookup"><span data-stu-id="181d3-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="181d3-121">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="181d3-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="181d3-122">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="181d3-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
