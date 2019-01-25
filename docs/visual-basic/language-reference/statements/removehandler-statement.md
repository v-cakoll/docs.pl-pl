---
title: RemoveHandler — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 27cdd2753507c6fc4d5c5041607e2ccb425b81b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560623"
---
# <a name="removehandler-statement"></a><span data-ttu-id="19c10-102">RemoveHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="19c10-102">RemoveHandler Statement</span></span>
<span data-ttu-id="19c10-103">Usuwa skojarzenie między zdarzeniem, a program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="19c10-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19c10-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19c10-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="19c10-105">Części</span><span class="sxs-lookup"><span data-stu-id="19c10-105">Parts</span></span>  
  
|<span data-ttu-id="19c10-106">Termin</span><span class="sxs-lookup"><span data-stu-id="19c10-106">Term</span></span>|<span data-ttu-id="19c10-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="19c10-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="19c10-108">Nazwa przetwarzanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19c10-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="19c10-109">Nazwa procedury obecnie obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="19c10-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19c10-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19c10-110">Remarks</span></span>  
 <span data-ttu-id="19c10-111">`AddHandler` i `RemoveHandler` instrukcje umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="19c10-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19c10-112">W przypadku zdarzeń niestandardowych instrukcja `RemoveHandler` wywołuje metodę dostępu zdarzenia `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="19c10-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="19c10-113">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="19c10-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19c10-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="19c10-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19c10-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19c10-115">See also</span></span>
- [<span data-ttu-id="19c10-116">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="19c10-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="19c10-117">Handles</span><span class="sxs-lookup"><span data-stu-id="19c10-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="19c10-118">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="19c10-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="19c10-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="19c10-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
