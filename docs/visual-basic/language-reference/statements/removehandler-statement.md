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
ms.openlocfilehash: 3a839a7d05d05066f6c0f774a683c8fc83c19643
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957722"
---
# <a name="removehandler-statement"></a><span data-ttu-id="e65b1-102">RemoveHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e65b1-102">RemoveHandler Statement</span></span>
<span data-ttu-id="e65b1-103">Usuwa skojarzenie między zdarzeniem a programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e65b1-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e65b1-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="e65b1-105">Części</span><span class="sxs-lookup"><span data-stu-id="e65b1-105">Parts</span></span>  
  
|<span data-ttu-id="e65b1-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e65b1-106">Term</span></span>|<span data-ttu-id="e65b1-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e65b1-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="e65b1-108">Nazwa obsługiwanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e65b1-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="e65b1-109">Nazwa procedury, która obecnie obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e65b1-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e65b1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e65b1-110">Remarks</span></span>  
 <span data-ttu-id="e65b1-111">Instrukcje `AddHandler` i`RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="e65b1-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e65b1-112">W przypadku zdarzeń niestandardowych instrukcja `RemoveHandler` wywołuje metodę dostępu zdarzenia `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="e65b1-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="e65b1-113">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e65b1-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e65b1-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="e65b1-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="e65b1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e65b1-115">See also</span></span>

- [<span data-ttu-id="e65b1-116">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e65b1-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="e65b1-117">Handles</span><span class="sxs-lookup"><span data-stu-id="e65b1-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="e65b1-118">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e65b1-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="e65b1-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e65b1-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
