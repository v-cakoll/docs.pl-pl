---
title: RaiseEvent — Instrukcja
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
ms.openlocfilehash: 19949fbdb1c1c54556876323d839b16fc01608f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605345"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="7a442-102">RaiseEvent — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a442-102">RaiseEvent Statement</span></span>
<span data-ttu-id="7a442-103">Wyzwala zdarzenie zadeklarowane na poziomie modułu w obrębie klasy, formularza lub dokumentu.</span><span class="sxs-lookup"><span data-stu-id="7a442-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a442-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7a442-104">Syntax</span></span>  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="7a442-105">Części</span><span class="sxs-lookup"><span data-stu-id="7a442-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="7a442-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7a442-106">Required.</span></span> <span data-ttu-id="7a442-107">Nazwa zdarzenia do wyzwalania.</span><span class="sxs-lookup"><span data-stu-id="7a442-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="7a442-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7a442-108">Optional.</span></span> <span data-ttu-id="7a442-109">Rozdzielana przecinkami lista zmiennych, tablic lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7a442-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="7a442-110">`argumentlist` Argument musi być ujęta w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="7a442-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="7a442-111">Jeśli nie ma żadnych argumentów, należy pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7a442-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a442-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7a442-112">Remarks</span></span>  
 <span data-ttu-id="7a442-113">Wymagane `eventname` zadeklarowano nazwę zdarzenia w module.</span><span class="sxs-lookup"><span data-stu-id="7a442-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="7a442-114">Wynika z konwencji nazewnictwa zmiennej języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7a442-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="7a442-115">Jeśli zdarzenie nie został zadeklarowany w module, w którym jest uruchamiany, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="7a442-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="7a442-116">Poniższy fragment kodu przedstawia deklaracji zdarzenia i procedury, w którym zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a442-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 <span data-ttu-id="7a442-117">Nie można użyć `RaiseEvent` wywołania zdarzeń, które nie są jawnie zadeklarowany w module.</span><span class="sxs-lookup"><span data-stu-id="7a442-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="7a442-118">Na przykład wszystkich formularzy dziedziczą <xref:System.Windows.Forms.Control.Click> zdarzenia z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, nie można zwiększyć za pomocą `RaiseEvent` w postaci pochodnych.</span><span class="sxs-lookup"><span data-stu-id="7a442-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="7a442-119">W przypadku `Click` zdarzenia w module formularza go zasłania własnych formularza <xref:System.Windows.Forms.Control.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a442-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="7a442-120">Nadal można wywołać formularza <xref:System.Windows.Forms.Control.Click> zdarzenia przez wywołanie metody <xref:System.Windows.Forms.Control.OnClick%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7a442-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="7a442-121">Domyślnie zdarzenia zdefiniowany w języku Visual Basic zgłasza jego programy obsługi zdarzeń w kolejności ustanowienie połączenia.</span><span class="sxs-lookup"><span data-stu-id="7a442-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="7a442-122">Ponieważ zdarzenia może mieć `ByRef` parametrów procesu, który łączy z opóźnieniem może pojawić się parametry, które zostały zmienione przez wcześniejszą obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a442-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="7a442-123">Po wykonywania programów obsługi zdarzeń, zwróceniem sterowania do procedury, która wywołała zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="7a442-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a442-124">Nieudostępnieni zdarzenia nie powinien być wywoływany w konstruktorze klasy, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="7a442-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="7a442-125">Chociaż takie zdarzenia nie powodują błędy środowiska wykonawczego, może nie powieść pod skojarzonej obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a442-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="7a442-126">Użyj `Shared` modyfikator, aby utworzyć udostępniony zdarzenie, chcąc wywołaj zdarzenie z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="7a442-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a442-127">Domyślne zachowanie zdarzenia można zmienić, definiując zdarzenie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="7a442-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="7a442-128">W przypadku niestandardowych zdarzeń `RaiseEvent` instrukcja wywołuje zdarzenie `RaiseEvent` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="7a442-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="7a442-129">Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7a442-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a442-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a442-130">Example</span></span>  
 <span data-ttu-id="7a442-131">W poniższym przykładzie użyto zdarzeń, aby liczba sekund od 10 do 0 w dół.</span><span class="sxs-lookup"><span data-stu-id="7a442-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="7a442-132">Kod przedstawia niektóre zdarzenia związane z metod, właściwości oraz instrukcje, w tym `RaiseEvent` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7a442-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="7a442-133">Źródło zdarzenia jest klasa, która wywołuje zdarzenie i metod, które przetwarzają zdarzenia obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a442-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="7a442-134">Źródło zdarzenia może mieć wielu obsług do zdarzeń, które generuje.</span><span class="sxs-lookup"><span data-stu-id="7a442-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="7a442-135">Po klasie zgłasza zdarzenie, że zdarzenie jest wywoływane dla każdej klasy, który został wybrany do obsługi zdarzeń dla tego wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7a442-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="7a442-136">W przykładzie użyto również formularza (`Form1`) z przyciskiem (`Button1`) i pola tekstowego (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="7a442-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="7a442-137">Po kliknięciu przycisku pierwsze pole tekstowe wyświetla odliczania od 10 do 0 sekund.</span><span class="sxs-lookup"><span data-stu-id="7a442-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="7a442-138">Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".</span><span class="sxs-lookup"><span data-stu-id="7a442-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="7a442-139">Kod `Form1` określa stany początkowych i końcowych formularza.</span><span class="sxs-lookup"><span data-stu-id="7a442-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="7a442-140">Zawiera również kod wykonywany w momencie pojawienia się zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7a442-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="7a442-141">Aby użyć tego przykładu, otwórz nowy projekt aplikacji systemu Windows, Dodawanie przycisku o nazwie `Button1` i pole tekstowe o nazwie `TextBox1` do formularza głównego o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7a442-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="7a442-142">Następnie kliknij prawym przyciskiem myszy formularz i kliknij przycisk **kod widoku** można otworzyć edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="7a442-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="7a442-143">Dodaj `WithEvents` zmienną do sekcji deklaracji `Form1` klasy.</span><span class="sxs-lookup"><span data-stu-id="7a442-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7a442-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="7a442-144">Example</span></span>  
 <span data-ttu-id="7a442-145">Dodaj następujący kod do kodu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="7a442-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="7a442-146">Zamień wszystkie zduplikowane procedur, które mogą istnieć, takich jak `Form_Load`, lub `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="7a442-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 <span data-ttu-id="7a442-147">Naciśnij klawisz F5, aby uruchomić poprzedni przykład i kliknij przycisk oznaczony **Start**.</span><span class="sxs-lookup"><span data-stu-id="7a442-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="7a442-148">Pierwsze pole tekstowe rozpoczyna odliczanie sekund.</span><span class="sxs-lookup"><span data-stu-id="7a442-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="7a442-149">Po upływie czasu pełny (10 sekund), pierwsze pole tekstowe wyświetla "Gotowe".</span><span class="sxs-lookup"><span data-stu-id="7a442-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a442-150">`My.Application.DoEvents` — Metoda nie przetwarza zdarzenia w taki sam sposób jak w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7a442-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="7a442-151">Aby zezwolić na formularzu, aby obsługiwać zdarzenia bezpośrednio, można użyć wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="7a442-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="7a442-152">Aby uzyskać więcej informacji, zobacz [wątki](../../programming-guide/concepts/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="7a442-152">For more information, see [Threading](../../programming-guide/concepts/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a442-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a442-153">See Also</span></span>  
 [<span data-ttu-id="7a442-154">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7a442-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="7a442-155">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a442-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="7a442-156">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a442-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="7a442-157">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7a442-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="7a442-158">Uchwyty</span><span class="sxs-lookup"><span data-stu-id="7a442-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
