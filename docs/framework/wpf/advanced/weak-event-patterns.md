---
title: Słabe wzorce zdarzeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f96327f8eaad36f3faebf48db083125816589821
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="weak-event-patterns"></a><span data-ttu-id="29e45-102">Słabe wzorce zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-102">Weak Event Patterns</span></span>
<span data-ttu-id="29e45-103">W aplikacjach istnieje możliwość, że programy obsługi, które są dołączone do źródła zdarzeń nie zostaną usunięte w połączeniu z obiektu odbiornika, który dołączyć program obsługi do źródła.</span><span class="sxs-lookup"><span data-stu-id="29e45-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="29e45-104">Taka sytuacja może prowadzić do przecieki pamięci.</span><span class="sxs-lookup"><span data-stu-id="29e45-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="29e45-105"> wprowadza wzorzec projektowania, który może służyć do rozwiązania tego problemu, zapewniając klasy Menedżera dedykowane dla konkretnego zdarzenia i implementowanie interfejsu na odbiorników dla tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="29e45-105"> introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="29e45-106">Ten wzorzec projektowy nosi nazwę *wzorzec słabe zdarzeń*.</span><span class="sxs-lookup"><span data-stu-id="29e45-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="29e45-107">Dlaczego implementują wzorzec słabe zdarzenia?</span><span class="sxs-lookup"><span data-stu-id="29e45-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="29e45-108">Nasłuchiwanie zdarzeń może prowadzić do przecieki pamięci.</span><span class="sxs-lookup"><span data-stu-id="29e45-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="29e45-109">Typowe techniki do nasłuchiwania zdarzeń jest należy użyć składni specyficzny dla języka, łączący program obsługi zdarzeń w źródle.</span><span class="sxs-lookup"><span data-stu-id="29e45-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="29e45-110">Na przykład w języku C#, że składnia jest: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="29e45-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="29e45-111">Ta metoda tworzy silne odwołanie ze źródła zdarzeń dla odbiornika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="29e45-112">Zwykle dołączanie program obsługi zdarzeń dla odbiornika powoduje, że odbiornika mają okres istnienia obiektu, który ma wpływ okres istnienia obiektu źródłowego (chyba że obsługi zdarzeń jest jawnie usunięte).</span><span class="sxs-lookup"><span data-stu-id="29e45-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="29e45-113">Jednak w pewnych okolicznościach może być okres istnienia obiektu nasłuchującego kontrolowany przez inne czynniki, takie jak obecnie przynależność do drzewa wizualnego aplikacji, a nie przez okres istnienia źródła.</span><span class="sxs-lookup"><span data-stu-id="29e45-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="29e45-114">Zawsze, gdy okres istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, ze wzorcem normalnego zdarzeń prowadzi do przeciek pamięci: odbiornika jest utrzymywane dłużej niż zamierzony.</span><span class="sxs-lookup"><span data-stu-id="29e45-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="29e45-115">Wzorzec słabe zdarzeń zaprojektowano w celu rozwiązania tego problemu przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="29e45-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="29e45-116">Wzorzec słabe zdarzeń można zawsze, gdy odbiornik musi zarejestrować zdarzenie, ale odbiornika nie może jawnie określić kiedy wyrejestrować.</span><span class="sxs-lookup"><span data-stu-id="29e45-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="29e45-117">Wzorzec słabe zdarzenia można również zawsze, gdy okres istnienia obiektu źródła przekracza okres istnienia obiektu przydatne odbiornika.</span><span class="sxs-lookup"><span data-stu-id="29e45-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="29e45-118">(W tym przypadku *przydatne* jest określany przez użytkownika.) Wzorzec słabe zdarzeń umożliwia odbiornika, aby zarejestrować i odbierać zdarzenia bez wpływu na właściwości okres istnienia obiektu nasłuchującego w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="29e45-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="29e45-119">W efekcie domniemanych odwołania ze źródła nie określa, czy odbiornik kwalifikuje się do pamięci.</span><span class="sxs-lookup"><span data-stu-id="29e45-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="29e45-120">Odwołanie jest słabe odwołanie, w związku z tym nazewnictwa wzorzec słabe zdarzeń i powiązanych [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="29e45-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="29e45-121">Odbiornik można odzyskiwanie zebrane lub w przeciwnym razie zniszczone i źródła można kontynuować bez zachowania noncollectible obsługi odwołania do obiektu teraz niszczone.</span><span class="sxs-lookup"><span data-stu-id="29e45-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="29e45-122">Kto powinien implementować wzorzec słabe zdarzenia?</span><span class="sxs-lookup"><span data-stu-id="29e45-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="29e45-123">Implementacja wzorca słabe zdarzeń jest ciekawe głównie dla autorów formantu.</span><span class="sxs-lookup"><span data-stu-id="29e45-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="29e45-124">Jako autor kontroli jesteś przede wszystkim odpowiedzialne za działanie i zawierania formantu i wpływu, jaki ma w przypadku aplikacji, w których zostanie on włożony.</span><span class="sxs-lookup"><span data-stu-id="29e45-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="29e45-125">W tym zachowanie okresu istnienia obiektu kontrolki, w szczególności obsługi problem przeciek pamięci opisem.</span><span class="sxs-lookup"><span data-stu-id="29e45-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="29e45-126">Niektóre scenariusze z założenia nadają się do aplikacji wzorzec słabe zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="29e45-127">Taki scenariusz jest powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="29e45-127">One such scenario is data binding.</span></span> <span data-ttu-id="29e45-128">W powiązaniu danych jest typowe dla obiekt źródłowy, być całkowicie niezależna od obiektu odbiornika, który jest elementem docelowym powiązania.</span><span class="sxs-lookup"><span data-stu-id="29e45-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="29e45-129">Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] już powiązania danych mają wzorzec słabe zdarzeń w implementowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="29e45-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="29e45-130">Jak zaimplementować wzorzec słabe zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="29e45-131">Istnieją trzy sposoby implementacji klienta wzorca słabe zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="29e45-132">Poniższa tabela zawiera listę trzech metod i zawiera pewne wskazówki dotyczące kiedy należy używać każdego.</span><span class="sxs-lookup"><span data-stu-id="29e45-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="29e45-133">Podejście</span><span class="sxs-lookup"><span data-stu-id="29e45-133">Approach</span></span>|<span data-ttu-id="29e45-134">Kiedy należy zaimplementować</span><span class="sxs-lookup"><span data-stu-id="29e45-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="29e45-135">Użyj istniejącej klasy Menedżera słabe zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="29e45-136">Jeśli chcesz subskrybować zdarzenie ma odpowiadające mu <xref:System.Windows.WeakEventManager>, użyj istniejącego menedżera słabe zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="29e45-137">Aby uzyskać listę menedżerów słabe zdarzeń, które są dołączone do WPF, zobacz w hierarchii dziedziczenia <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="29e45-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="29e45-138">Należy jednak pamiętać, że są względnie mało menedżerów słabe zdarzeń dołączonych WPF, dzięki czemu prawdopodobnie trzeba wybrać jeden z innych metod.</span><span class="sxs-lookup"><span data-stu-id="29e45-138">Note, however, that there are relatively few weak event managers that are included with WPF, so you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="29e45-139">Używanie klasy Menedżera ogólnego słabe zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="29e45-140">Użyj ogólnego <xref:System.Windows.WeakEventManager%602> kiedy istniejący <xref:System.Windows.WeakEventManager> jest nie jest dostępny, chcesz w prosty sposób wdrożenia, które nie mają danych o wydajności.</span><span class="sxs-lookup"><span data-stu-id="29e45-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="29e45-141">Ogólnego <xref:System.Windows.WeakEventManager%602> jest mniej wydajne niż Menedżer zdarzeń słabe istniejących lub niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="29e45-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="29e45-142">Na przykład klasa ogólna ma więcej odbicia do odnajdywania zdarzenie otrzymuje nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="29e45-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="29e45-143">Ponadto kod, aby zarejestrować zdarzenia przy użyciu ogólnej <xref:System.Windows.WeakEventManager%602> jest bardziej pełne niż przy użyciu istniejącej lub niestandardowych <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="29e45-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="29e45-144">Utwórz klasę Menedżera słabe zdarzenie niestandardowe</span><span class="sxs-lookup"><span data-stu-id="29e45-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="29e45-145">Utworzenie niestandardowego <xref:System.Windows.WeakEventManager> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępna i ma najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="29e45-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="29e45-146">Przy użyciu niestandardowego <xref:System.Windows.WeakEventManager> Aby subskrybować zdarzenia będą bardziej wydajne, ale ponoszenia kosztów więcej kod na początku.</span><span class="sxs-lookup"><span data-stu-id="29e45-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
  
 <span data-ttu-id="29e45-147">W poniższych sekcjach opisano sposobu implementacji wzorca słabe zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-147">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="29e45-148">Dla celów tej dyskusji Aby subskrybować zdarzenia o następujących cechach.</span><span class="sxs-lookup"><span data-stu-id="29e45-148">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
-   <span data-ttu-id="29e45-149">Nazwa zdarzenia `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="29e45-149">The event name is `SomeEvent`.</span></span>  
  
-   <span data-ttu-id="29e45-150">Zdarzenie jest zgłaszane przez `EventSource` klasy.</span><span class="sxs-lookup"><span data-stu-id="29e45-150">The event is raised by the `EventSource` class.</span></span>  
  
-   <span data-ttu-id="29e45-151">Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="29e45-151">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
-   <span data-ttu-id="29e45-152">Parametr typu przekazuje zdarzenia `SomeEventEventArgs` do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="29e45-152">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="29e45-153">Przy użyciu istniejącej klasy słabe Menedżer zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-153">Using an Existing Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="29e45-154">Znajdź zdarzenia słabe istniejącego menedżera.</span><span class="sxs-lookup"><span data-stu-id="29e45-154">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="29e45-155">Aby uzyskać listę menedżerów słabe zdarzeń, które są dołączone do WPF, zobacz w hierarchii dziedziczenia <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="29e45-155">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2.  <span data-ttu-id="29e45-156">Użyj nowego Menedżera słabe zdarzeń zamiast podłączenie zdarzenia normalnego.</span><span class="sxs-lookup"><span data-stu-id="29e45-156">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="29e45-157">Jeśli na przykład następujący wzór używa Twój kod, aby subskrybować zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="29e45-157">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="29e45-158">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="29e45-158">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="29e45-159">Podobnie jeśli kod używa następującego wzorca do anulowania subskrypcji na zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="29e45-159">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="29e45-160">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="29e45-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="29e45-161">Przy użyciu klasy ogólnej słabe Menedżer zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-161">Using the Generic Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="29e45-162">Użyj ogólnych <xref:System.Windows.WeakEventManager%602> klasy zamiast podłączenie zdarzenia normalnego.</span><span class="sxs-lookup"><span data-stu-id="29e45-162">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="29e45-163">Jeśli używasz <xref:System.Windows.WeakEventManager%602> zarejestrować odbiorników zdarzeń, podać źródło zdarzenia i <xref:System.EventArgs> typu jako parametrów typu klasy i wywołanie <xref:System.Windows.WeakEventManager%602.AddHandler%2A> zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="29e45-163">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="29e45-164">Tworzenie niestandardowych słabe klasy Menedżer zdarzeń</span><span class="sxs-lookup"><span data-stu-id="29e45-164">Creating a Custom Weak Event Manager Class</span></span>  
  
1.  <span data-ttu-id="29e45-165">Skopiuj następujący szablon klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="29e45-165">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="29e45-166">Ta klasa dziedziczy <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="29e45-166">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2.  <span data-ttu-id="29e45-167">Zastąp `SomeEventWeakEventManager` nazwa z własnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="29e45-167">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3.  <span data-ttu-id="29e45-168">Zamień nazwy trzech opisanych wcześniej odpowiadają nazwom wydarzenia.</span><span class="sxs-lookup"><span data-stu-id="29e45-168">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="29e45-169">(`SomeEvent`, `EventSource`, i `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="29e45-169">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4.  <span data-ttu-id="29e45-170">Ustawić widoczność (publiczne / wewnętrzne / prywatnej) klasy słabe zdarzeń Menedżera taką samą widoczność jak zdarzenia, którymi zarządza.</span><span class="sxs-lookup"><span data-stu-id="29e45-170">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5.  <span data-ttu-id="29e45-171">Użyj nowego Menedżera słabe zdarzeń zamiast podłączenie zdarzenia normalnego.</span><span class="sxs-lookup"><span data-stu-id="29e45-171">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="29e45-172">Jeśli na przykład następujący wzór używa Twój kod, aby subskrybować zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="29e45-172">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="29e45-173">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="29e45-173">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="29e45-174">Podobnie jeśli kod używa następującego wzorca do anulowania subskrypcji na zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="29e45-174">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="29e45-175">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="29e45-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="29e45-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29e45-176">See Also</span></span>  
 <xref:System.Windows.WeakEventManager>  
 <xref:System.Windows.IWeakEventListener>  
 [<span data-ttu-id="29e45-177">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="29e45-177">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="29e45-178">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="29e45-178">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)
