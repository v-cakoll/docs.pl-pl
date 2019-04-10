---
title: Deklarowanie i wywoływanie zdarzeń (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: cab6c90947eae8abeb9387535eadb2f89e71454a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320694"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="23786-102">Przewodnik: Deklarowanie i wywoływanie zdarzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23786-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="23786-103">W tym instruktażu pokazano, jak deklarowanie i wywoływanie zdarzeń klasy o nazwie `Widget`.</span><span class="sxs-lookup"><span data-stu-id="23786-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="23786-104">Po wykonaniu kroków, warto przeczytać temat Pomocnika [instruktażu: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), który pokazuje, jak używać zdarzeń z `Widget` obiektów, aby zapewnić informacje o stanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23786-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="23786-105">Klasa elementu Widget</span><span class="sxs-lookup"><span data-stu-id="23786-105">The Widget Class</span></span>  
 <span data-ttu-id="23786-106">Przyjęto założenie, do momentu, w którym masz `Widget` klasy.</span><span class="sxs-lookup"><span data-stu-id="23786-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="23786-107">Twoje `Widget` klasa zawiera metody, która może zająć dużo czasu wykonania i chcesz, aby aplikację, aby można było oferowane pewnego rodzaju zakończenia wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="23786-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="23786-108">Oczywiście można dokonać `Widget` obiektu Wyświetla okno dialogowe procent ukończenia, ale następnie może być zapoznaniu się z tego okna dialogowego każdego projektu, w którym użyto `Widget` klasy.</span><span class="sxs-lookup"><span data-stu-id="23786-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="23786-109">Dobre zasada konstrukcja obiektu funkcyjnego jest umożliwienie aplikacji, która używa na uchwyt obiektu interfejsu użytkownika — chyba że całego obiektu ma na celu zarządzanie pole formularza lub okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="23786-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="23786-110">Celem `Widget` jest do innych zadań, aby go lepiej jest dodać `PercentDone` zdarzeń, dzięki czemu procedury, która wywołuje `Widget`jego metody obsługi, zdarzeń i wyświetlania stanu aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="23786-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="23786-111">`PercentDone` Zdarzenia może również udostępniać mechanizm anuluje zadanie.</span><span class="sxs-lookup"><span data-stu-id="23786-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="23786-112">Aby zbudować przykład kodu, w tym temacie</span><span class="sxs-lookup"><span data-stu-id="23786-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="23786-113">Otwórz nowy projekt aplikacji Windows Visual Basic i Utwórz formularz o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="23786-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="23786-114">Dodawanie dwóch przycisków i etykiety w celu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="23786-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="23786-115">Nazwy obiektów, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="23786-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="23786-116">Obiekt</span><span class="sxs-lookup"><span data-stu-id="23786-116">Object</span></span>|<span data-ttu-id="23786-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="23786-117">Property</span></span>|<span data-ttu-id="23786-118">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="23786-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="23786-119">Zadanie podrzędne uruchamiania</span><span class="sxs-lookup"><span data-stu-id="23786-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="23786-120">Anuluj</span><span class="sxs-lookup"><span data-stu-id="23786-120">Cancel</span></span>|  
    |`Label`|`(Name)`<span data-ttu-id="23786-121">,</span><span class="sxs-lookup"><span data-stu-id="23786-121">,</span></span> `Text`|<span data-ttu-id="23786-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="23786-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="23786-123">Na **projektu** menu, wybierz **Dodaj klasę** można dodać klasę o nazwie `Widget.vb` do projektu.</span><span class="sxs-lookup"><span data-stu-id="23786-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="23786-124">Aby zadeklarować zdarzenia dla klasy elementu Widget</span><span class="sxs-lookup"><span data-stu-id="23786-124">To declare an event for the Widget class</span></span>  
  
-   <span data-ttu-id="23786-125">Użyj `Event` — słowo kluczowe, aby zadeklarować zdarzenia w `Widget` klasy.</span><span class="sxs-lookup"><span data-stu-id="23786-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="23786-126">Należy zauważyć, że zdarzenie może mieć `ByVal` i `ByRef` argumentów, jako `Widget`firmy `PercentDone` pokazuje zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="23786-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="23786-127">Gdy obiekt wywołujący odbiera `PercentDone` zdarzenia `Percent` argument zawiera procent wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="23786-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="23786-128">`Cancel` Argument może być równa `True` anulować metodę, która wywołała zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="23786-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23786-129">Można zadeklarować argumenty zdarzenia, tak jak argumenty procedur z następującymi wyjątkami: Zdarzenia nie może mieć `Optional` lub `ParamArray` argumentów i zdarzenia nie mają zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="23786-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="23786-130">`PercentDone` Wydarzenie jest podniesione przez `LongTask` metody `Widget` klasy.</span><span class="sxs-lookup"><span data-stu-id="23786-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> `LongTask` <span data-ttu-id="23786-131">przyjmuje dwa argumenty: czas metody udaje się pracy, a minimalny interwał czasowy przed `LongTask` wstrzymuje działanie, aby podnieść `PercentDone` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23786-131">takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="23786-132">Aby zgłosić zdarzenie PercentDone</span><span class="sxs-lookup"><span data-stu-id="23786-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="23786-133">Aby uprościć dostęp do `Timer` Dodaj właściwość używana przez tę klasę `Imports` instrukcji na górze sekcji deklaracji klasy modułu, powyżej `Class Widget` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="23786-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="23786-134">Dodaj następujący kod do `Widget` klasy:</span><span class="sxs-lookup"><span data-stu-id="23786-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="23786-135">Gdy Twoja aplikacja wywołuje `LongTask` metody `Widget` klasy wywołuje `PercentDone` zdarzeń co `MinimumInterval` sekund.</span><span class="sxs-lookup"><span data-stu-id="23786-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="23786-136">Po powrocie z zdarzenia `LongTask` sprawdza, czy `Cancel` argumentów została ustawiona na `True`.</span><span class="sxs-lookup"><span data-stu-id="23786-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="23786-137">Kilka zastrzeżenia są niezbędne, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="23786-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="23786-138">Dla uproszczenia `LongTask` procedurze przyjęto założenie, wcześniej wiadomo jak długo potrwa zadania.</span><span class="sxs-lookup"><span data-stu-id="23786-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="23786-139">Prawie nigdy nie jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="23786-139">This is almost never the case.</span></span> <span data-ttu-id="23786-140">Podzielenie zadania na fragmenty o rozmiarze nawet może być trudne, a często najistotniejszych dla użytkowników jest po prostu ilość czasu, jaki upływa zanim staną się wskazanie, że coś, co dzieje się.</span><span class="sxs-lookup"><span data-stu-id="23786-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="23786-141">W tym przykładzie może mieć wykrył innego wady.</span><span class="sxs-lookup"><span data-stu-id="23786-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="23786-142">`Timer` Właściwość zwraca liczbę sekund, które upłynęły od północy; w związku z tym, aplikacja zablokowania, gdy zostanie uruchomiona po prostu wcześniejszą niż północ.</span><span class="sxs-lookup"><span data-stu-id="23786-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="23786-143">Bardziej dokładnej podejście do pomiaru czasu przenoszące warunków ograniczających, takie jak to pod uwagę lub uniknąć je całkowicie, przy użyciu właściwości, takich jak `Now`.</span><span class="sxs-lookup"><span data-stu-id="23786-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="23786-144">Teraz, gdy `Widget` klasy może wywoływać zdarzenia, można przenieść do poniższych wskazówek.</span><span class="sxs-lookup"><span data-stu-id="23786-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="23786-145">[Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje sposób użycia `WithEvents` skojarzyć program obsługi zdarzeń za pomocą `PercentDone` zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="23786-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23786-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23786-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="23786-147">Przewodnik: Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="23786-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="23786-148">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="23786-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
