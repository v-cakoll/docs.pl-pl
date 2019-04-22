---
title: AddHandler — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 1e8d8f512f163d82f074a5ad53fbb38a10904dfa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827084"
---
# <a name="addhandler-statement"></a><span data-ttu-id="5e0d4-102">AddHandler — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e0d4-102">AddHandler Statement</span></span>
<span data-ttu-id="5e0d4-103">Kojarzy zdarzenie z programem obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e0d4-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="5e0d4-105">Części</span><span class="sxs-lookup"><span data-stu-id="5e0d4-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="5e0d4-106">zdarzenie</span><span class="sxs-lookup"><span data-stu-id="5e0d4-106">event</span></span>|<span data-ttu-id="5e0d4-107">Nazwa zdarzenia do obsługi.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="5e0d4-108">Nazwa procedury, która obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="5e0d4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e0d4-109">Remarks</span></span>  
 <span data-ttu-id="5e0d4-110">Instrukcje `AddHandler` i `RemoveHandler` umożliwiają uruchamianie i zatrzymywanie obsługi zdarzeń w dowolnym czasie podczas wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="5e0d4-111">Podpis procedury `eventhandler` musi być zgodny z podpisem zdarzenia `event`.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="5e0d4-112">Zarówno słowo kluczowe `Handles`, jak i instrukcja `AddHandler` umożliwiają określenie konkretnych procedur do obsługi konkretnych zdarzeń, ale występują tu pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="5e0d4-113">Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="5e0d4-114">Słowa kluczowego `Handles` należy użyć podczas definiowania procedury, aby określić, że ma ona obsługiwać konkretne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="5e0d4-115">Aby uzyskać więcej informacji, zobacz artykuł [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)</span><span class="sxs-lookup"><span data-stu-id="5e0d4-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e0d4-116">W przypadku zdarzeń niestandardowych instrukcja `AddHandler` wywołuje metodę dostępu zdarzenia `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="5e0d4-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="5e0d4-117">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="5e0d4-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e0d4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e0d4-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="5e0d4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e0d4-119">See also</span></span>

- [<span data-ttu-id="5e0d4-120">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e0d4-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="5e0d4-121">Handles</span><span class="sxs-lookup"><span data-stu-id="5e0d4-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="5e0d4-122">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e0d4-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="5e0d4-123">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="5e0d4-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
