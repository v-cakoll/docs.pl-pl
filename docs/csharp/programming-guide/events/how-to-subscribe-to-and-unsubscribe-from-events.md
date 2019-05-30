---
title: 'Instrukcje: Subskrybowanie i anulowanie subskrypcji zdarzeń - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 365ea55a112a4a04964a8271f2f7e5591a3b0d5d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301042"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="b255f-102">Instrukcje: Subskrybowanie i anulowanie subskrypcji zdarzeń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="b255f-102">How to: Subscribe to and Unsubscribe from Events (C# Programming Guide)</span></span>
<span data-ttu-id="b255f-103">Subskrybowanie zdarzenia, które jest opublikowane przez inną klasę napisać kod niestandardowy, który jest wywoływana, gdy zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="b255f-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="b255f-104">Na przykład może subskrybować przycisku `click` zdarzeń, aby zapewnić aplikacji zrobić coś, co jest przydatne, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="b255f-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="b255f-105">Aby subskrybować zdarzenia przy użyciu programu Visual Studio IDE</span><span class="sxs-lookup"><span data-stu-id="b255f-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="b255f-106">Jeśli nie widzisz **właściwości** okna w **projektowania** wyświetlić, kliknij prawym przyciskiem myszy formularza lub kontrolki, dla której chcesz utworzyć program obsługi zdarzeń, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b255f-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="b255f-107">W górnej części **właściwości** okna, kliknij przycisk **zdarzenia** ikony.</span><span class="sxs-lookup"><span data-stu-id="b255f-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="b255f-108">Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b255f-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="b255f-109">Visual C# tworzy metodę programu obsługi zdarzeń pusty i dodaje go do kodu.</span><span class="sxs-lookup"><span data-stu-id="b255f-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="b255f-110">Alternatywnie można dodać kod ręcznie w **kodu** widoku.</span><span class="sxs-lookup"><span data-stu-id="b255f-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="b255f-111">Na przykład następujące wiersze kodu Zadeklaruj metodę programu obsługi zdarzeń, która zostanie wywołana kiedy `Form` klasy wywołuje `Load` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b255f-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="b255f-112">Wiersz kodu, który jest wymagany do subskrybowania zdarzenia jest automatycznie generowany w `InitializeComponent` metody w pliku Form1.Designer.cs w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b255f-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="b255f-113">Przypomina to:</span><span class="sxs-lookup"><span data-stu-id="b255f-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="b255f-114">Aby subskrybować zdarzenia programowe</span><span class="sxs-lookup"><span data-stu-id="b255f-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="b255f-115">Zdefiniuj metodę programu obsługi zdarzeń, którego podpis odpowiadają podpisowi delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b255f-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="b255f-116">Na przykład, jeśli zdarzenie jest oparty na <xref:System.EventHandler> typ delegata, poniższy kod przedstawia szkieletu metody:</span><span class="sxs-lookup"><span data-stu-id="b255f-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="b255f-117">Użyj operator przypisania dodawania (`+=`) do dołączenia programu obsługi zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b255f-117">Use the addition assignment operator (`+=`) to attach your event handler to the event.</span></span> <span data-ttu-id="b255f-118">W poniższym przykładzie przyjęto założenie, że obiekt o nazwie `publisher` posiada zdarzenie o nazwie `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="b255f-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="b255f-119">Należy pamiętać, że klasy subskrybenta wymaga odwołania do klasy wydawcy Aby subskrybować ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="b255f-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="b255f-120">Należy pamiętać, że składnia poprzednich jest nowego w języku C# w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b255f-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="b255f-121">Jest to równoważne dokładnie składni języka C# 1.0, w którym hermetyzowany delegata należy jawnie utworzyć przy użyciu `new` — słowo kluczowe:</span><span class="sxs-lookup"><span data-stu-id="b255f-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="b255f-122">Program obsługi zdarzeń mogą być również dodawane za pomocą wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="b255f-122">An event handler can also be added by using a lambda expression:</span></span>  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     <span data-ttu-id="b255f-123">Aby uzyskać więcej informacji, zobacz [jak: Użycie wyrażeń Lambda poza LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span><span class="sxs-lookup"><span data-stu-id="b255f-123">For more information, see [How to: Use Lambda Expressions Outside LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).</span></span>  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="b255f-124">Aby subskrybować zdarzenia przy użyciu metody anonimowej</span><span class="sxs-lookup"><span data-stu-id="b255f-124">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="b255f-125">Jeśli nie trzeba będzie później anulować subskrypcję zdarzenia, można użyć operator przypisania dodawania (`+=`) można dołączyć metodę anonimową na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b255f-125">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="b255f-126">W poniższym przykładzie przyjęto założenie, że obiekt o nazwie `publisher` posiada zdarzenie o nazwie `RaiseCustomEvent` i `CustomEventArgs` klasy została zdefiniowana również przeprowadzenie pewnego rodzaju informacji o zdarzeniach specjalne.</span><span class="sxs-lookup"><span data-stu-id="b255f-126">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="b255f-127">Należy pamiętać, że klasa subskrybenta wymaga odwołania do `publisher` Aby subskrybować ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="b255f-127">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="b255f-128">Należy zauważyć, że nie można łatwo anulować zdarzenie Jeśli funkcja anonimowa jest używany do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="b255f-128">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="b255f-129">Aby anulować subskrypcję, w tym scenariuszu, należy przejść do kodu, gdzie możesz subskrybować zdarzenie, Zapisz metody anonimowej w zmiennej delegata, a następnie dodaj delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b255f-129">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="b255f-130">Ogólnie rzecz biorąc zaleca się, że nie należy używać funkcji anonimowych do subskrybowania zdarzenia, jeśli będzie konieczne anulowanie subskrypcji zdarzeń w pewnym momencie później w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b255f-130">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="b255f-131">Aby uzyskać więcej informacji na temat funkcji anonimowych zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b255f-131">For more information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="b255f-132">Anulowanie subskrypcji</span><span class="sxs-lookup"><span data-stu-id="b255f-132">Unsubscribing</span></span>  
 <span data-ttu-id="b255f-133">Aby zapobiec sytuacji, w której obsługi zdarzenia są wywoływane, gdy zdarzenie jest wywoływane, Anuluj subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b255f-133">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="b255f-134">Aby zapobiec przeciekom zasobów, anulujesz subskrypcję zdarzeń przed usunięcia obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="b255f-134">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="b255f-135">Dopóki nie można anulować subskrypcję zdarzenia, delegatów multiemisji, źródłową zdarzeń w obiekcie publikowania odwołuje się do delegata, który hermetyzuje programu obsługi zdarzeń subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="b255f-135">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="b255f-136">Tak długo, jak obiekt publikowania zawiera odwołanie do tego, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="b255f-136">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="b255f-137">Aby anulować subskrypcję zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b255f-137">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="b255f-138">Użyj operator przypisania odejmowania (`-=`), aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="b255f-138">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="b255f-139">Gdy wszyscy subskrybenci została anulowana zdarzenie, wystąpienie zdarzenia w klasie wydawca jest ustawiona na `null`.</span><span class="sxs-lookup"><span data-stu-id="b255f-139">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b255f-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b255f-140">See also</span></span>

- [<span data-ttu-id="b255f-141">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="b255f-141">Events</span></span>](../../../csharp/programming-guide/events/index.md)
- [<span data-ttu-id="b255f-142">event</span><span class="sxs-lookup"><span data-stu-id="b255f-142">event</span></span>](../../../csharp/language-reference/keywords/event.md)
- [<span data-ttu-id="b255f-143">Instrukcje: Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b255f-143">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="b255f-144">— i Operatorzy-=</span><span class="sxs-lookup"><span data-stu-id="b255f-144">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="b255f-145">+ i operatory +=</span><span class="sxs-lookup"><span data-stu-id="b255f-145">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
