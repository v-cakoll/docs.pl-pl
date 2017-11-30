---
title: "Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52b4b6ca8b03d8301535d6aeedc3bd0190d8527f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="25dc2-102">Porady: wywoływanie programu do obsługi zdarzeń w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25dc2-102">How to: Call an Event Handler in Visual Basic</span></span>
<span data-ttu-id="25dc2-103">*Zdarzeń* jest akcji lub wystąpienie — takie jak myszy przekroczony kliknij lub limit kredytu — który jest rozpoznawany przez inny składnik programu i dla którego można napisać kod do odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="25dc2-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="25dc2-104">*Obsługi zdarzeń* jest zapisywany kod, aby odpowiadać na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="25dc2-104">An *event handler* is the code you write to respond to an event.</span></span>  
  
 <span data-ttu-id="25dc2-105">Program obsługi zdarzeń w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jest `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="25dc2-105">An event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is a `Sub` procedure.</span></span> <span data-ttu-id="25dc2-106">Jednak możesz nie zwykle wywołują go taki sam sposób jak inne `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="25dc2-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="25dc2-107">Zamiast tego należy zidentyfikować procedury obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="25dc2-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="25dc2-108">Można to zrobić za pomocą [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli i [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) zmiennej lub [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25dc2-108">You can do this either with a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="25dc2-109">Przy użyciu `Handles` klauzula jest domyślną metodą Aby zadeklarować program obsługi zdarzeń w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="25dc2-109">Using a `Handles` clause is the default way to declare an event handler in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="25dc2-110">Jest to sposób obsługi zdarzeń są zapisywane przez projektantów podczas programowania zintegrowane środowisko programistyczne (IDE).</span><span class="sxs-lookup"><span data-stu-id="25dc2-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="25dc2-111">`AddHandler` Instrukcja jest odpowiedni dla wywoływanie zdarzeń dynamicznie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="25dc2-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>  
  
 <span data-ttu-id="25dc2-112">Po wystąpieniu zdarzenia, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatycznie wywołuje procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="25dc2-112">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the event handler procedure.</span></span> <span data-ttu-id="25dc2-113">Wszelki kod, który ma dostęp do zdarzenia mogą spowodować on wystąpić, wykonując [RaiseEvent — instrukcja](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25dc2-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).</span></span>  
  
 <span data-ttu-id="25dc2-114">Z tego samego zdarzenia można skojarzyć więcej niż jeden program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="25dc2-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="25dc2-115">W niektórych przypadkach można skojarzenie obsługi z zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="25dc2-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="25dc2-116">Aby uzyskać więcej informacji, zobacz [zdarzenia](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="25dc2-116">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="25dc2-117">Aby wywołać przy użyciu dojścia i WithEvents program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="25dc2-117">To call an event handler using Handles and WithEvents</span></span>  
  
1.  <span data-ttu-id="25dc2-118">Upewnij się, że zdarzenie jest zadeklarowany za pomocą [Event — instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25dc2-118">Make sure the event is declared with an [Event Statement](../../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
2.  <span data-ttu-id="25dc2-119">Deklarowanie zmiennej obiektu w module lub klasy poziomu przy użyciu [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="25dc2-119">Declare an object variable at module or class level, using the [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="25dc2-120">`As` Klauzula dla tej zmiennej musi określać klasy, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="25dc2-120">The `As` clause for this variable must specify the class that raises the event.</span></span>  
  
3.  <span data-ttu-id="25dc2-121">W deklaracji obsługi zdarzeń `Sub` procedury dodawania [obsługuje](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli, która określa `WithEvents` zmienną i nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="25dc2-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>  
  
4.  <span data-ttu-id="25dc2-122">Po wystąpieniu zdarzenia, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatycznie wywołuje `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="25dc2-122">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="25dc2-123">Można użyć kodu `RaiseEvent` oświadczenie wystąpić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="25dc2-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="25dc2-124">W poniższym przykładzie zdefiniowano zdarzenia i `WithEvents` zmiennej, która odwołuje się do klasy, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="25dc2-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="25dc2-125">Obsługa zdarzeń `Sub` używa procedury `Handles` klauzuli, aby określić klasę i obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="25dc2-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="25dc2-126">Aby wywołać przy użyciu metody AddHandler program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="25dc2-126">To call an event handler using AddHandler</span></span>  
  
1.  <span data-ttu-id="25dc2-127">Upewnij się, że zdarzenie jest zadeklarowany za pomocą `Event` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="25dc2-127">Make sure the event is declared with an `Event` statement.</span></span>  
  
2.  <span data-ttu-id="25dc2-128">Wykonanie [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nawiązać dynamicznie obsługi zdarzeń `Sub` procedury ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="25dc2-128">Execute an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>  
  
3.  <span data-ttu-id="25dc2-129">Po wystąpieniu zdarzenia, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatycznie wywołuje `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="25dc2-129">When the event occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="25dc2-130">Można użyć kodu `RaiseEvent` oświadczenie wystąpić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="25dc2-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>  
  
     <span data-ttu-id="25dc2-131">W poniższym przykładzie zdefiniowano `Sub` procedury obsługi <xref:System.Windows.Forms.Form.Closing> zdarzeń formularza.</span><span class="sxs-lookup"><span data-stu-id="25dc2-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="25dc2-132">Następnie używa [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md) do skojarzenia `catchClose` procedury obsługi zdarzeń dla <xref:System.Windows.Forms.Form.Closing>.</span><span class="sxs-lookup"><span data-stu-id="25dc2-132">It then uses the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     <span data-ttu-id="25dc2-133">Usuń skojarzenie program obsługi zdarzeń z zdarzenie, wykonując [RemoveHandler — instrukcja](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="25dc2-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../../visual-basic/language-reference/statements/removehandler-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25dc2-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25dc2-134">See Also</span></span>  
 [<span data-ttu-id="25dc2-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="25dc2-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="25dc2-136">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="25dc2-136">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="25dc2-137">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="25dc2-137">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="25dc2-138">AddressOf — Operator</span><span class="sxs-lookup"><span data-stu-id="25dc2-138">AddressOf Operator</span></span>](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="25dc2-139">Porady: Tworzenie procedury</span><span class="sxs-lookup"><span data-stu-id="25dc2-139">How to: Create a Procedure</span></span>](./how-to-create-a-procedure.md)  
 [<span data-ttu-id="25dc2-140">Porady: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="25dc2-140">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
