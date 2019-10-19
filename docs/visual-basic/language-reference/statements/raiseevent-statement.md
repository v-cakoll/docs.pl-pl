---
title: RaiseEvent — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: efc7da34a297fd01411302b717cfda83aa9f87d2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582095"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="92b29-102">RaiseEvent — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="92b29-102">RaiseEvent Statement</span></span>
<span data-ttu-id="92b29-103">Wyzwala zdarzenie zadeklarowane na poziomie modułu w klasie, formularzu lub dokumencie.</span><span class="sxs-lookup"><span data-stu-id="92b29-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92b29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92b29-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="92b29-105">Części</span><span class="sxs-lookup"><span data-stu-id="92b29-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="92b29-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="92b29-106">Required.</span></span> <span data-ttu-id="92b29-107">Nazwa zdarzenia do wyzwolenia.</span><span class="sxs-lookup"><span data-stu-id="92b29-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="92b29-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="92b29-108">Optional.</span></span> <span data-ttu-id="92b29-109">Rozdzielana przecinkami lista zmiennych, tablic lub wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="92b29-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="92b29-110">Argument `argumentlist` musi być ujęty w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="92b29-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="92b29-111">Jeśli nie ma żadnych argumentów, nawiasy muszą być pominięte.</span><span class="sxs-lookup"><span data-stu-id="92b29-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92b29-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92b29-112">Remarks</span></span>  
 <span data-ttu-id="92b29-113">Wymagana `eventname` to nazwa zdarzenia zadeklarowanego w module.</span><span class="sxs-lookup"><span data-stu-id="92b29-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="92b29-114">Następuje Visual Basic konwencji nazewnictwa zmiennych.</span><span class="sxs-lookup"><span data-stu-id="92b29-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="92b29-115">Jeśli zdarzenie nie zostało zadeklarowane w module, w którym jest wywoływany, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="92b29-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="92b29-116">Poniższy fragment kodu ilustruje deklarację zdarzenia i procedurę, w której zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="92b29-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="92b29-117">Nie można użyć `RaiseEvent` do wywołania zdarzeń, które nie są jawnie zadeklarowane w module.</span><span class="sxs-lookup"><span data-stu-id="92b29-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="92b29-118">Na przykład, wszystkie formularze dziedziczą zdarzenie <xref:System.Windows.Forms.Control.Click> od <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nie można go podwyższyć przy użyciu `RaiseEvent` w formularzu pochodnym.</span><span class="sxs-lookup"><span data-stu-id="92b29-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="92b29-119">Jeśli zadeklarujesz zdarzenie `Click` w module formularza, będzie ono zasłaniać własne zdarzenie <xref:System.Windows.Forms.Control.Click> formularza.</span><span class="sxs-lookup"><span data-stu-id="92b29-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="92b29-120">Nadal można wywołać zdarzenie <xref:System.Windows.Forms.Control.Click> formularza, wywołując metodę <xref:System.Windows.Forms.Control.OnClick%2A>.</span><span class="sxs-lookup"><span data-stu-id="92b29-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="92b29-121">Domyślnie zdarzenie zdefiniowane w Visual Basic wywołuje obsługę zdarzeń w kolejności, w jakiej są nawiązywane połączenia.</span><span class="sxs-lookup"><span data-stu-id="92b29-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="92b29-122">Ponieważ zdarzenia mogą mieć `ByRef` parametry, proces, który nawiązuje połączenie, może odbierać parametry, które zostały zmienione przez wcześniejszą procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="92b29-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="92b29-123">Po wykonaniu obsługi zdarzeń sterowanie jest zwracane do procedury podrzędnej, która wywołała zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="92b29-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92b29-124">Nie można podwyższyć poziomu zdarzeń nieudostępnionych w konstruktorze klasy, w której są zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="92b29-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="92b29-125">Chociaż takie zdarzenia nie powodują błędów w czasie wykonywania, mogą one nie zostać przechwycone przez skojarzone programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="92b29-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="92b29-126">Użyj modyfikatora `Shared`, aby utworzyć zdarzenie udostępnione, jeśli trzeba zgłosić zdarzenie z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="92b29-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92b29-127">Domyślne zachowanie zdarzeń można zmienić przez zdefiniowanie niestandardowego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92b29-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="92b29-128">W przypadku zdarzeń niestandardowych instrukcja `RaiseEvent` wywołuje metodę dostępu `RaiseEvent` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="92b29-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="92b29-129">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="92b29-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92b29-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="92b29-130">Example</span></span>  
 <span data-ttu-id="92b29-131">Poniższy przykład używa zdarzeń do zliczenia w dół sekund od 10 do 0.</span><span class="sxs-lookup"><span data-stu-id="92b29-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="92b29-132">Kod ilustruje kilka metod, właściwości i instrukcji związanych ze zdarzeniami, w tym instrukcji `RaiseEvent`.</span><span class="sxs-lookup"><span data-stu-id="92b29-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="92b29-133">Klasa, która wywołuje zdarzenie, jest źródłem zdarzenia, a metody, które przetwarzają zdarzenie, są procedurami obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="92b29-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="92b29-134">Źródło zdarzenia może mieć wiele programów obsługi dla generowanych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="92b29-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="92b29-135">Gdy Klasa zgłasza zdarzenie, to zdarzenie jest zgłaszane dla każdej klasy, która została wybrana do obsługi zdarzeń dla tego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="92b29-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="92b29-136">W przykładzie zastosowano również formularz (`Form1`) z przyciskiem (`Button1`) i polem tekstowym (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="92b29-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="92b29-137">Po kliknięciu przycisku, pierwsze pole tekstowe Wyświetla odliczanie od 10 do 0 sekund.</span><span class="sxs-lookup"><span data-stu-id="92b29-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="92b29-138">Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".</span><span class="sxs-lookup"><span data-stu-id="92b29-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="92b29-139">Kod dla `Form1` określa początkowe i końcowe Stany formularza.</span><span class="sxs-lookup"><span data-stu-id="92b29-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="92b29-140">Zawiera również kod wykonywany, gdy zdarzenia są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="92b29-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="92b29-141">Aby użyć tego przykładu, Otwórz nowy projekt aplikacji systemu Windows, Dodaj przycisk o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="92b29-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="92b29-142">Następnie kliknij prawym przyciskiem myszy formularz i kliknij polecenie **Wyświetl kod** , aby otworzyć Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="92b29-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="92b29-143">Dodaj zmienną `WithEvents` do sekcji deklaracji klasy `Form1`.</span><span class="sxs-lookup"><span data-stu-id="92b29-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="92b29-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="92b29-144">Example</span></span>  
 <span data-ttu-id="92b29-145">Dodaj następujący kod do kodu dla `Form1`.</span><span class="sxs-lookup"><span data-stu-id="92b29-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="92b29-146">Zastąp wszystkie zduplikowane procedury, takie jak `Form_Load` lub `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="92b29-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="92b29-147">Naciśnij klawisz F5, aby uruchomić poprzedni przykład, a następnie kliknij przycisk zatytułowany **Uruchom**.</span><span class="sxs-lookup"><span data-stu-id="92b29-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="92b29-148">Pierwsze pole tekstowe zaczyna przeliczać sekundy w dół.</span><span class="sxs-lookup"><span data-stu-id="92b29-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="92b29-149">Gdy upłynął pełny czas (10 sekund), pierwsze pole tekstowe wyświetla "gotowe".</span><span class="sxs-lookup"><span data-stu-id="92b29-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92b29-150">Metoda `My.Application.DoEvents` nie przetwarza zdarzeń w taki sam sposób jak w przypadku formularza.</span><span class="sxs-lookup"><span data-stu-id="92b29-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="92b29-151">Aby umożliwić bezpośrednie obsługiwanie zdarzeń przez formularz, można użyć wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="92b29-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="92b29-152">Aby uzyskać więcej informacji, zobacz sekcję [zarządzane wątki](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="92b29-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b29-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92b29-153">See also</span></span>

- [<span data-ttu-id="92b29-154">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="92b29-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="92b29-155">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="92b29-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="92b29-156">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="92b29-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="92b29-157">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="92b29-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="92b29-158">Realizuj</span><span class="sxs-lookup"><span data-stu-id="92b29-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
