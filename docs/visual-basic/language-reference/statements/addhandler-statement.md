---
title: AddHandler — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004542"
---
# <a name="addhandler-statement"></a><span data-ttu-id="37fc9-102">AddHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="37fc9-102">AddHandler Statement</span></span>
<span data-ttu-id="37fc9-103">Kojarzy zdarzenie z programem obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37fc9-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37fc9-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="37fc9-105">Części</span><span class="sxs-lookup"><span data-stu-id="37fc9-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="37fc9-106">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="37fc9-106">event</span></span>|<span data-ttu-id="37fc9-107">Nazwa zdarzenia do obsłużenia.</span><span class="sxs-lookup"><span data-stu-id="37fc9-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="37fc9-108">Nazwa procedury, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="37fc9-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="37fc9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37fc9-109">Remarks</span></span>  
 <span data-ttu-id="37fc9-110">Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="37fc9-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="37fc9-111">Sygnatura procedury `eventhandler` musi być zgodna z sygnaturą zdarzenia `event`.</span><span class="sxs-lookup"><span data-stu-id="37fc9-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="37fc9-112">Słowo kluczowe `Handles` i instrukcja `AddHandler` umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="37fc9-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="37fc9-113">Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="37fc9-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="37fc9-114">Użyj słowa kluczowego `Handles` podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="37fc9-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="37fc9-115">Aby uzyskać więcej informacji, zobacz [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="37fc9-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37fc9-116">W przypadku zdarzeń niestandardowych instrukcja `AddHandler` wywołuje metodę dostępu `AddHandler` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="37fc9-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="37fc9-117">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="37fc9-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37fc9-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="37fc9-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="37fc9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="37fc9-119">See also</span></span>

- [<span data-ttu-id="37fc9-120">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37fc9-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="37fc9-121">Realizuj</span><span class="sxs-lookup"><span data-stu-id="37fc9-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="37fc9-122">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="37fc9-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="37fc9-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="37fc9-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
