---
title: Jak subskrybować i wypisać się ze zdarzeń - Przewodnik po programowaniu C#
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705330"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="38f1c-102">Jak subskrybować i anulować subskrypcję zdarzeń (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="38f1c-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="38f1c-103">Subskrybujesz zdarzenie, które jest publikowane przez inną klasę, gdy chcesz napisać kod niestandardowy, który jest wywoływany, gdy to zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="38f1c-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="38f1c-104">Na przykład można zapisać się do `click` zdarzenia przycisku w celu aplikacji zrobić coś pożytecznego, gdy użytkownik kliknie przycisk.</span><span class="sxs-lookup"><span data-stu-id="38f1c-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="38f1c-105">Aby subskrybować zdarzenia przy użyciu ide programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="38f1c-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="38f1c-106">Jeśli nie widzisz okna **Właściwości,** w **widoku projektowym** kliknij prawym przyciskiem myszy formularz lub formant, dla którego chcesz utworzyć program obsługi zdarzeń, a następnie wybierz pozycję **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="38f1c-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="38f1c-107">Na górze okna **Właściwości** kliknij ikonę **Zdarzenia.**</span><span class="sxs-lookup"><span data-stu-id="38f1c-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="38f1c-108">Kliknij dwukrotnie zdarzenie, które chcesz utworzyć, `Load` na przykład zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="38f1c-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="38f1c-109">Visual C# tworzy metodę obsługi zdarzeń puste i dodaje go do kodu.</span><span class="sxs-lookup"><span data-stu-id="38f1c-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="38f1c-110">Alternatywnie można dodać kod ręcznie w **widoku kod.**</span><span class="sxs-lookup"><span data-stu-id="38f1c-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="38f1c-111">Na przykład następujące wiersze kodu deklarują metodę obsługi zdarzeń, która zostanie wywołana, `Form` gdy klasa wywołuje `Load` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="38f1c-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="38f1c-112">Wiersz kodu, który jest wymagany do subskrybowania zdarzenia `InitializeComponent` jest również automatycznie generowany w metodzie w pliku Form1.Designer.cs w projekcie.</span><span class="sxs-lookup"><span data-stu-id="38f1c-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="38f1c-113">Przypomina to:</span><span class="sxs-lookup"><span data-stu-id="38f1c-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="38f1c-114">Aby programowo subskrybować zdarzenia</span><span class="sxs-lookup"><span data-stu-id="38f1c-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="38f1c-115">Zdefiniuj metodę obsługi zdarzeń, której podpis pasuje do podpisu delegata dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38f1c-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="38f1c-116">Na przykład jeśli zdarzenie jest <xref:System.EventHandler> oparte na typie delegata, następujący kod reprezentuje wycinek metody:</span><span class="sxs-lookup"><span data-stu-id="38f1c-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="38f1c-117">Użyj operatora przypisania`+=`dodawania ( ) do dołączenia programu obsługi zdarzeń do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38f1c-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="38f1c-118">W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent`.</span><span class="sxs-lookup"><span data-stu-id="38f1c-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="38f1c-119">Należy zauważyć, że klasa subskrybenta wymaga odwołania do klasy wydawcy, aby subskrybować jego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38f1c-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="38f1c-120">Należy zauważyć, że poprzednia składnia jest nowa w języku C# 2.0.</span><span class="sxs-lookup"><span data-stu-id="38f1c-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="38f1c-121">Jest to dokładnie odpowiednik składni C# 1.0, w którym encapsulating delegata `new` muszą być jawnie utworzone przy użyciu słowa kluczowego:</span><span class="sxs-lookup"><span data-stu-id="38f1c-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="38f1c-122">Można również użyć [wyrażenia lambda,](../statements-expressions-operators/lambda-expressions.md) aby określić program obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="38f1c-122">You also can use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
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
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="38f1c-123">Aby subskrybować zdarzenia przy użyciu metody anonimowej</span><span class="sxs-lookup"><span data-stu-id="38f1c-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="38f1c-124">Jeśli nie będziesz musiał zrezygnować z subskrypcji zdarzenia później, możesz`+=`użyć operatora przypisania dodawania ( ) aby dołączyć do zdarzenia metodę anonimową.</span><span class="sxs-lookup"><span data-stu-id="38f1c-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="38f1c-125">W poniższym przykładzie załóżmy, że obiekt o nazwie `publisher` ma zdarzenie o nazwie `RaiseCustomEvent` i że `CustomEventArgs` klasa została również zdefiniowana do przenoszenia jakiegoś specjalistycznego informacji o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="38f1c-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="38f1c-126">Należy zauważyć, że klasa subskrybenta wymaga odwołania do, `publisher` aby zapisać się do jego zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="38f1c-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="38f1c-127">Ważne jest, aby zauważyć, że nie można łatwo zrezygnować z subskrypcji zdarzenia, jeśli używasz funkcji anonimowej, aby go zapisać.</span><span class="sxs-lookup"><span data-stu-id="38f1c-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="38f1c-128">Aby anulować subskrypcję w tym scenariuszu, należy wrócić do kodu, w którym subskrybujesz zdarzenie, przechowuj metodę anonimową w zmiennej delegata, a następnie dodaj pełnomocnika do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38f1c-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="38f1c-129">Ogólnie rzecz biorąc, zaleca się, aby nie używać funkcji anonimowych do subskrybowania zdarzeń, jeśli będziesz musiał zrezygnować z subskrypcji zdarzenia w późniejszym momencie w kodzie.</span><span class="sxs-lookup"><span data-stu-id="38f1c-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="38f1c-130">Aby uzyskać więcej informacji na temat funkcji anonimowych, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="38f1c-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="38f1c-131">Anulowanie subskrypcji</span><span class="sxs-lookup"><span data-stu-id="38f1c-131">Unsubscribing</span></span>  
 <span data-ttu-id="38f1c-132">Aby zapobiec wywoływaniu programu obsługi zdarzeń po wywołaniu zdarzenia, anuluj subskrypcję ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="38f1c-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="38f1c-133">Aby zapobiec wyciekom zasobów, należy anulować subskrypcję ze zdarzeń przed utylizacji obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="38f1c-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="38f1c-134">Dopóki nie anulujesz subskrypcji zdarzenia, delegat multiemisji, który leży u podstaw zdarzenia w obiekcie publikowania, ma odwołanie do pełnomocnika, który hermetyzuje program obsługi zdarzeń subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="38f1c-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="38f1c-135">Tak długo, jak obiekt publikowania przechowuje tego odwołania, wyrzucanie elementów bezużytecznych nie spowoduje usunięcia obiektu subskrybenta.</span><span class="sxs-lookup"><span data-stu-id="38f1c-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="38f1c-136">Aby anulować subskrypcję wydarzenia</span><span class="sxs-lookup"><span data-stu-id="38f1c-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="38f1c-137">Użyj operatora przypisania`-=`odejmowania ( ) aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="38f1c-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="38f1c-138">Gdy wszyscy subskrybenci zrezygnowali z subskrypcji `null`zdarzenia, wystąpienie zdarzenia w klasie wydawcy jest ustawione na .</span><span class="sxs-lookup"><span data-stu-id="38f1c-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f1c-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="38f1c-139">See also</span></span>

- [<span data-ttu-id="38f1c-140">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="38f1c-140">Events</span></span>](./index.md)
- [<span data-ttu-id="38f1c-141">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="38f1c-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="38f1c-142">Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38f1c-142">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="38f1c-143">- i -= operatory</span><span class="sxs-lookup"><span data-stu-id="38f1c-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="38f1c-144">+ i += operatory</span><span class="sxs-lookup"><span data-stu-id="38f1c-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
