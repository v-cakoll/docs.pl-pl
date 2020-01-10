---
title: Jak subskrybować i anulować subskrypcję zdarzeń — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705330"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="04787-102">Subskrybowanie i anulowanie subskrypcji zdarzeń (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="04787-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="04787-103">Zasubskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać niestandardowy kod, który jest wywoływany, gdy zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="04787-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="04787-104">Na przykład możesz subskrybować zdarzenie `click` przycisku, aby aplikacja była przydatna, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="04787-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="04787-105">Aby subskrybować zdarzenia za pomocą środowiska IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04787-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="04787-106">Jeśli nie widzisz okna **Właściwości** , w widoku **projektu** kliknij prawym przyciskiem myszy formularz lub kontrolkę, dla której chcesz utworzyć procedurę obsługi zdarzeń, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="04787-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="04787-107">W górnej części okna **Właściwości** kliknij ikonę **zdarzenia** .</span><span class="sxs-lookup"><span data-stu-id="04787-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="04787-108">Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, na przykład zdarzenie `Load`.</span><span class="sxs-lookup"><span data-stu-id="04787-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="04787-109">Wizualizacja C# tworzy pustą metodę obsługi zdarzeń i dodaje ją do kodu.</span><span class="sxs-lookup"><span data-stu-id="04787-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="04787-110">Alternatywnie możesz dodać kod ręcznie w widoku **kodu** .</span><span class="sxs-lookup"><span data-stu-id="04787-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="04787-111">Na przykład następujące wiersze kodu deklarują metodę procedury obsługi zdarzeń, która zostanie wywołana, gdy Klasa `Form` zgłasza zdarzenie `Load`.</span><span class="sxs-lookup"><span data-stu-id="04787-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="04787-112">Wiersz kodu, który jest wymagany do subskrybowania zdarzenia jest również automatycznie generowany w metodzie `InitializeComponent` w pliku Form1.Designer.cs w projekcie.</span><span class="sxs-lookup"><span data-stu-id="04787-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="04787-113">Przypomina to:</span><span class="sxs-lookup"><span data-stu-id="04787-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="04787-114">Aby programowo subskrybować zdarzenia</span><span class="sxs-lookup"><span data-stu-id="04787-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="04787-115">Zdefiniuj metodę procedury obsługi zdarzeń, której sygnatura pasuje do sygnatury delegata zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="04787-116">Na przykład, jeśli zdarzenie jest oparte na typie delegata <xref:System.EventHandler>, poniższy kod reprezentuje element zastępczy metody:</span><span class="sxs-lookup"><span data-stu-id="04787-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="04787-117">Użyj operatora przypisania dodawania (`+=`), aby dołączyć procedurę obsługi zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="04787-118">W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="04787-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="04787-119">Należy zauważyć, że Klasa subskrybenta wymaga odwołania do klasy wydawcy w celu subskrybowania jego zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="04787-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="04787-120">Należy pamiętać, że poprzednia składnia C# jest nowa w 2,0.</span><span class="sxs-lookup"><span data-stu-id="04787-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="04787-121">Jest to dokładnie równoważne składni C# 1,0, w której delegata hermetyzowania musi być jawnie utworzona za pomocą słowa kluczowego `new`:</span><span class="sxs-lookup"><span data-stu-id="04787-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="04787-122">Można również użyć [wyrażenia lambda](../statements-expressions-operators/lambda-expressions.md) do określenia programu obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="04787-122">You also can use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="04787-123">Aby subskrybować zdarzenia za pomocą metody anonimowej</span><span class="sxs-lookup"><span data-stu-id="04787-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="04787-124">Jeśli nie musisz anulować subskrybowania zdarzenia później, możesz użyć operatora przypisania dodawania (`+=`) do dołączenia anonimowej metody do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="04787-125">W poniższym przykładzie Załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że Klasa `CustomEventArgs` została również zdefiniowana do przeprowadzenia pewnego rodzaju specjalistycznych informacji o zdarzeniu.</span><span class="sxs-lookup"><span data-stu-id="04787-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="04787-126">Należy zauważyć, że Klasa subskrybenta wymaga odwołania do `publisher`, aby subskrybować jego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="04787-127">Należy pamiętać, że nie można łatwo anulować subskrypcji zdarzenia, jeśli użyto anonimowej funkcji do subskrybowania.</span><span class="sxs-lookup"><span data-stu-id="04787-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="04787-128">Aby anulować subskrypcję w tym scenariuszu, należy wrócić do kodu, w którym subskrybujesz zdarzenie, zapisać metodę anonimową w zmiennej delegata, a następnie dodać delegata do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="04787-129">Ogólnie rzecz biorąc, firma Microsoft zaleca, aby nie używać funkcji anonimowych do subskrybowania zdarzeń, jeśli będzie konieczne anulowanie subskrypcji zdarzenia w pewnym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="04787-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="04787-130">Aby uzyskać więcej informacji na temat funkcji anonimowych, zobacz [funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="04787-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="04787-131">Anulowanie subskrypcji</span><span class="sxs-lookup"><span data-stu-id="04787-131">Unsubscribing</span></span>  
 <span data-ttu-id="04787-132">Aby uniemożliwić wywoływanie programu obsługi zdarzeń po podniesieniu zdarzenia, Anuluj subskrypcję zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="04787-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="04787-133">Aby zapobiec przeciekom zasobów, należy anulować subskrypcję zdarzeń przed usunięciem obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="04787-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="04787-134">Dopóki nie subskrybujesz zdarzenia, delegat multiemisji, który opiera się na zdarzeniu w obiekcie do publikowania, ma odwołanie do delegata, który hermetyzuje procedurę obsługi zdarzeń subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="04787-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="04787-135">Tak długo, jak obiekt publikacji przechowuje to odwołanie, wyrzucanie elementów bezużytecznych nie usunie obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="04787-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="04787-136">Aby anulować subskrypcję zdarzenia</span><span class="sxs-lookup"><span data-stu-id="04787-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="04787-137">Użyj operatora przypisywania odejmowania (`-=`), aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="04787-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="04787-138">Gdy Wszyscy subskrybenci nie subskrybują zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawione na `null`.</span><span class="sxs-lookup"><span data-stu-id="04787-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04787-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04787-139">See also</span></span>

- [<span data-ttu-id="04787-140">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="04787-140">Events</span></span>](./index.md)
- [<span data-ttu-id="04787-141">event</span><span class="sxs-lookup"><span data-stu-id="04787-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="04787-142">Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="04787-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="04787-143">Operatory-and-=</span><span class="sxs-lookup"><span data-stu-id="04787-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="04787-144">Operatory + i + =</span><span class="sxs-lookup"><span data-stu-id="04787-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
