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
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582025"
---
# <a name="removehandler-statement"></a><span data-ttu-id="97350-102">RemoveHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="97350-102">RemoveHandler Statement</span></span>
<span data-ttu-id="97350-103">Usuwa skojarzenie między zdarzeniem a programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="97350-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97350-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97350-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="97350-105">Części</span><span class="sxs-lookup"><span data-stu-id="97350-105">Parts</span></span>  
  
|<span data-ttu-id="97350-106">Termin</span><span class="sxs-lookup"><span data-stu-id="97350-106">Term</span></span>|<span data-ttu-id="97350-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="97350-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="97350-108">Nazwa obsługiwanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="97350-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="97350-109">Nazwa procedury, która obecnie obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="97350-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="97350-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97350-110">Remarks</span></span>  
 <span data-ttu-id="97350-111">Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="97350-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97350-112">W przypadku zdarzeń niestandardowych instrukcja `RemoveHandler` wywołuje metodę dostępu `RemoveHandler` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="97350-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="97350-113">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="97350-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="97350-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="97350-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="97350-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97350-115">See also</span></span>

- [<span data-ttu-id="97350-116">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="97350-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="97350-117">Realizuj</span><span class="sxs-lookup"><span data-stu-id="97350-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="97350-118">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="97350-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="97350-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="97350-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
