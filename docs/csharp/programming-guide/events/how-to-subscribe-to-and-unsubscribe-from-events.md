---
title: 'Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ecb65a2156f83d9da722329ff6159bb08e464eaa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="13cfa-102">Porady: subskrybowanie i anulowanie subskrypcji zdarzeń (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="13cfa-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="13cfa-103">Subskrybować zdarzenia, które są publikowane przez inną klasę, umożliwia pisanie kodu niestandardowego, który jest wywoływany, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="13cfa-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="13cfa-104">Na przykład może subskrybować przycisk `click` zdarzeń, aby zwiększyć bezpieczeństwo aplikacji Zrób coś, które są przydatne, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="13cfa-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="13cfa-105">Aby subskrybować zdarzenia za pomocą środowiska IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13cfa-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1.  <span data-ttu-id="13cfa-106">Jeśli nie widzisz **właściwości** okna w **projekt** wyświetlić, kliknij prawym przyciskiem myszy formularz lub formant, dla którego chcesz utworzyć program obsługi zdarzeń, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="13cfa-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="13cfa-107">Nad **właściwości** okna, kliknij przycisk **zdarzenia** ikony.</span><span class="sxs-lookup"><span data-stu-id="13cfa-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3.  <span data-ttu-id="13cfa-108">Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13cfa-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="13cfa-109">Visual C# tworzy metoda obsługi zdarzeń pusty i dodaje go do kodu.</span><span class="sxs-lookup"><span data-stu-id="13cfa-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="13cfa-110">Alternatywnie można dodać ręcznie w kodzie **kod** widoku.</span><span class="sxs-lookup"><span data-stu-id="13cfa-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="13cfa-111">Na przykład następujące wiersze kodu zadeklarować metoda obsługi zdarzeń, która zostanie wywołana podczas `Form` klasy zgłasza `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13cfa-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     <span data-ttu-id="13cfa-112">Wiersz kodu, który jest wymagany, aby subskrybować zdarzenia jest automatycznie generowany w `InitializeComponent` metody w pliku Form1.Designer.cs w projekcie.</span><span class="sxs-lookup"><span data-stu-id="13cfa-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="13cfa-113">Przypomina to:</span><span class="sxs-lookup"><span data-stu-id="13cfa-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="13cfa-114">Aby subskrybować zdarzenia programowo</span><span class="sxs-lookup"><span data-stu-id="13cfa-114">To subscribe to events programmatically</span></span>  
  
1.  <span data-ttu-id="13cfa-115">Zdefiniuj metoda obsługi zdarzeń, których Podpis pasuje do podpisu delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="13cfa-116">Na przykład, jeśli zdarzenie jest oparta na <xref:System.EventHandler> typ delegata, poniższy kod przedstawia szkieletu metody:</span><span class="sxs-lookup"><span data-stu-id="13cfa-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  <span data-ttu-id="13cfa-117">Użyj operator przypisania dodawania (`+=`) można dołączyć obsługi zdarzenia do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="13cfa-118">W poniższym przykładzie założono, że obiekt o nazwie `publisher` ma zdarzenia o nazwie `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="13cfa-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="13cfa-119">Należy pamiętać, że klasa subskrybenta wymaga odwołania do klasy wydawcy, aby subskrybować jego zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13cfa-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="13cfa-120">Należy pamiętać, że składnia poprzedniej nowego w języku C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="13cfa-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="13cfa-121">Jest dokładnym odpowiednikiem składni 1.0 C#, w której hermetyzowany delegata musi jawnie utworzone za pomocą `new` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="13cfa-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="13cfa-122">Program obsługi zdarzeń można również dodać za pomocą wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="13cfa-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="13cfa-123">Aby uzyskać więcej informacji, zobacz [porady: użycie Lambda wyrażenia poza LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="13cfa-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="13cfa-124">Aby subskrybować zdarzenia za pomocą metody anonimowej</span><span class="sxs-lookup"><span data-stu-id="13cfa-124">To subscribe to events by using an anonymous method</span></span>  
  
-   <span data-ttu-id="13cfa-125">Jeśli nie musisz anulować subskrypcję później na zdarzenie, można użyć operator przypisania dodawania (`+=`) można dołączyć do zdarzenia metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="13cfa-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="13cfa-126">W poniższym przykładzie założono, że obiekt o nazwie `publisher` ma zdarzenia o nazwie `RaiseCustomEvent` oraz że `CustomEventArgs` klasa została zdefiniowana również do przenoszenia określonego rodzaju informacje dotyczące specjalnych zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="13cfa-127">Należy pamiętać, że klasa subskrybenta wymaga odwołania do `publisher` Aby subskrybować jego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="13cfa-128">Należy zauważyć, że nie można łatwo anulować zdarzenie użycie funkcji anonimowej jego subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="13cfa-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="13cfa-129">Aby anulować subskrypcję, w tym scenariuszu, należy go z powrotem do kodu, w którym subskrybować zdarzenia, metodą anonimową należy przechowywać w zmiennej obiektu delegowanego, a następnie dodaj delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="13cfa-130">Ogólnie rzecz biorąc zaleca się, że nie należy używać funkcji anonimowych Aby subskrybować zdarzenia, jeśli konieczne będzie anulowanie subskrypcji zdarzeń w pewnym momencie nowsze w kodzie.</span><span class="sxs-lookup"><span data-stu-id="13cfa-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="13cfa-131">Aby uzyskać więcej informacji na temat funkcji anonimowych zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="13cfa-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="13cfa-132">Anulowanie</span><span class="sxs-lookup"><span data-stu-id="13cfa-132">Unsubscribing</span></span>  
 <span data-ttu-id="13cfa-133">Aby zapobiec obsługi zdarzenia jest wywoływane, gdy zdarzenie jest zgłaszane, subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="13cfa-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="13cfa-134">Aby zapobiec przecieków zasobów, anulujesz subskrypcję zdarzenia przed usunięcia obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="13cfa-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="13cfa-135">Dopóki subskrypcję zdarzeń, delegat multiemisji źródłową zdarzeń w obiekcie publikowania odwołuje się do delegata, który hermetyzuje abonenta obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="13cfa-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="13cfa-136">Tak długo, jak obiekt publikowania zawiera odwołanie do tego, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="13cfa-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="13cfa-137">Aby anulować subskrypcję zdarzenia</span><span class="sxs-lookup"><span data-stu-id="13cfa-137">To unsubscribe from an event</span></span>  
  
-   <span data-ttu-id="13cfa-138">Użyj operator przypisania odejmowania (`-=`) na anulowanie subskrypcji zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="13cfa-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="13cfa-139">Po wszystkich subskrybentów została anulowana zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawiany na `null`.</span><span class="sxs-lookup"><span data-stu-id="13cfa-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13cfa-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13cfa-140">See Also</span></span>  
 [<span data-ttu-id="13cfa-141">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="13cfa-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="13cfa-142">event</span><span class="sxs-lookup"><span data-stu-id="13cfa-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)  
 [<span data-ttu-id="13cfa-143">Instrukcje: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="13cfa-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [<span data-ttu-id="13cfa-144">-= — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="13cfa-144">-= Operator (C# Reference)</span></span>](../../language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="13cfa-145">+=, operator</span><span class="sxs-lookup"><span data-stu-id="13cfa-145">+= Operator</span></span>](../../../csharp/language-reference/operators/addition-assignment-operator.md)