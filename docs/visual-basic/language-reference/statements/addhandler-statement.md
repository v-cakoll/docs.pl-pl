---
title: AddHandler — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350190"
---
# <a name="addhandler-statement"></a><span data-ttu-id="31d73-102">AddHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="31d73-102">AddHandler Statement</span></span>
<span data-ttu-id="31d73-103">Kojarzy zdarzenie z programem obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="31d73-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31d73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="31d73-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="31d73-105">Części</span><span class="sxs-lookup"><span data-stu-id="31d73-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="31d73-106">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="31d73-106">event</span></span>|<span data-ttu-id="31d73-107">Nazwa zdarzenia do obsłużenia.</span><span class="sxs-lookup"><span data-stu-id="31d73-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="31d73-108">Nazwa procedury, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="31d73-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="31d73-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="31d73-109">Remarks</span></span>  
 <span data-ttu-id="31d73-110">Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w dowolnym momencie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="31d73-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="31d73-111">Sygnatura procedury `eventhandler` musi być zgodna z sygnaturą `event`zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31d73-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="31d73-112">Słowo kluczowe `Handles` i instrukcja `AddHandler` umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="31d73-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="31d73-113">Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="31d73-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="31d73-114">Użyj słowa kluczowego `Handles` podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="31d73-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="31d73-115">Aby uzyskać więcej informacji, zobacz [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="31d73-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31d73-116">W przypadku zdarzeń niestandardowych instrukcja `AddHandler` wywołuje metodę dostępu `AddHandler` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="31d73-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="31d73-117">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31d73-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="31d73-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="31d73-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="31d73-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31d73-119">See also</span></span>

- [<span data-ttu-id="31d73-120">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="31d73-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="31d73-121">Realizuj</span><span class="sxs-lookup"><span data-stu-id="31d73-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="31d73-122">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="31d73-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="31d73-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="31d73-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
