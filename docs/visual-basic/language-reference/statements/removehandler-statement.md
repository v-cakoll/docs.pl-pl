---
title: RemoveHandler — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404255"
---
# <a name="removehandler-statement"></a><span data-ttu-id="724ef-102">RemoveHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="724ef-102">RemoveHandler Statement</span></span>
<span data-ttu-id="724ef-103">Usuwa skojarzenie między zdarzeniem a programem obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="724ef-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="724ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="724ef-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="724ef-105">Części</span><span class="sxs-lookup"><span data-stu-id="724ef-105">Parts</span></span>  
  
|<span data-ttu-id="724ef-106">Termin</span><span class="sxs-lookup"><span data-stu-id="724ef-106">Term</span></span>|<span data-ttu-id="724ef-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="724ef-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="724ef-108">Nazwa obsługiwanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="724ef-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="724ef-109">Nazwa procedury, która obecnie obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="724ef-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="724ef-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="724ef-110">Remarks</span></span>  
 <span data-ttu-id="724ef-111">`AddHandler`Instrukcje i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń dla określonego zdarzenia w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="724ef-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="724ef-112">W przypadku zdarzeń niestandardowych `RemoveHandler` instrukcja wywołuje `RemoveHandler` metodę dostępu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="724ef-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="724ef-113">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="724ef-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="724ef-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="724ef-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="724ef-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="724ef-115">See also</span></span>

- [<span data-ttu-id="724ef-116">AddHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="724ef-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="724ef-117">Handles</span><span class="sxs-lookup"><span data-stu-id="724ef-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="724ef-118">Event — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="724ef-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="724ef-119">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="724ef-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
