---
title: "RemoveHandler — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="532e9-102">RemoveHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="532e9-102">RemoveHandler Statement</span></span>
<span data-ttu-id="532e9-103">Usuwa skojarzenie między zdarzeniem i program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="532e9-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="532e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="532e9-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="532e9-105">Części</span><span class="sxs-lookup"><span data-stu-id="532e9-105">Parts</span></span>  
  
|<span data-ttu-id="532e9-106">Termin</span><span class="sxs-lookup"><span data-stu-id="532e9-106">Term</span></span>|<span data-ttu-id="532e9-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="532e9-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="532e9-108">Nazwa zdarzenia, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="532e9-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="532e9-109">Nazwa procedury obecnie obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="532e9-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="532e9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="532e9-110">Remarks</span></span>  
 <span data-ttu-id="532e9-111">`AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w czasie wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="532e9-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="532e9-112">W przypadku niestandardowych zdarzeń `RemoveHandler` instrukcja wywołuje zdarzenie `RemoveHandler` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="532e9-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="532e9-113">Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="532e9-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="532e9-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="532e9-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="532e9-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="532e9-115">See Also</span></span>  
 [<span data-ttu-id="532e9-116">AddHandler — instrukcja</span><span class="sxs-lookup"><span data-stu-id="532e9-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="532e9-117">Uchwyty</span><span class="sxs-lookup"><span data-stu-id="532e9-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="532e9-118">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="532e9-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="532e9-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="532e9-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
