---
title: Słabe wzorce zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 9f61a5a60b2ba1305158d1ab570079fe6aac19ac
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870743"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="32b43-102">Słabe wzorce zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-102">Weak Event Patterns</span></span>
<span data-ttu-id="32b43-103">W aplikacjach jest możliwe, że programy obsługi dołączone do źródeł zdarzeń nie zostaną zniszczone w koordynacji z obiektem odbiornika, który dołączył program obsługi do źródła.</span><span class="sxs-lookup"><span data-stu-id="32b43-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="32b43-104">Ta sytuacja może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="32b43-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="32b43-105">wprowadza Wzorzec projektowy, który może służyć do rozwiązywania tego problemu, dostarczając dedykowaną klasę Menedżera dla określonych zdarzeń i implementując interfejs w detektorach dla tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="32b43-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="32b43-106">Ten Wzorzec projektowy jest znany jako *słaby wzorzec zdarzeń*.</span><span class="sxs-lookup"><span data-stu-id="32b43-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="32b43-107">Dlaczego warto zaimplementować słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="32b43-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="32b43-108">Nasłuchiwanie zdarzeń może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="32b43-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="32b43-109">Typową techniką nasłuchiwania zdarzeń jest użycie składni charakterystycznej dla języka, która dołącza procedurę obsługi do zdarzenia w źródle.</span><span class="sxs-lookup"><span data-stu-id="32b43-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="32b43-110">Na przykład w programie C#składnia jest następująca: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="32b43-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="32b43-111">Ta technika tworzy silne odwołanie ze źródła zdarzenia do odbiornika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="32b43-112">Zwykle dołączenie obsługi zdarzeń dla odbiornika powoduje, że odbiornik ma czas istnienia obiektu, na który ma wpływ okres istnienia obiektu (chyba że program obsługi zdarzeń został jawnie usunięty).</span><span class="sxs-lookup"><span data-stu-id="32b43-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="32b43-113">W pewnych okolicznościach może być konieczne, aby okres istnienia obiektu odbiornika był kontrolowany przez inne czynniki, na przykład czy należy on do drzewa wizualnego aplikacji, a nie przez okres istnienia źródła.</span><span class="sxs-lookup"><span data-stu-id="32b43-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="32b43-114">Za każdym razem, gdy okres istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, normalny wzorzec zdarzenia prowadzi do przecieku pamięci: odbiornik działa dłużej niż zamierzone.</span><span class="sxs-lookup"><span data-stu-id="32b43-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="32b43-115">Niesłaby wzorzec zdarzeń został zaprojektowany w celu rozwiązania tego problemu przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="32b43-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="32b43-116">Wzorca zdarzeń słabych można użyć zawsze, gdy odbiornik musi zarejestrować się na potrzeby zdarzenia, ale odbiornik nie wie jawnie, kiedy należy wyrejestrować.</span><span class="sxs-lookup"><span data-stu-id="32b43-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="32b43-117">Wzorca zdarzeń słabych można również użyć zawsze, gdy okres istnienia obiektu źródła przekracza użyteczny okres istnienia odbiornika.</span><span class="sxs-lookup"><span data-stu-id="32b43-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="32b43-118">(W tym przypadku jest to *przydatne* przez użytkownika). Słaby wzorzec zdarzeń umożliwia odbiornikowi rejestrowanie i odbieranie zdarzenia bez wpływu na charakterystykę okresu istnienia obiektu odbiornika w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="32b43-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="32b43-119">W efekcie odwołanie implikowane ze źródła nie określa, czy odbiornik kwalifikuje się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="32b43-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="32b43-120">Odwołanie to słabe odwołanie, w związku z czym nazwa słabego wzorca zdarzeń i powiązane interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="32b43-120">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="32b43-121">Odbiornik może być wyrzucony lub zniszczony w inny sposób, a źródło może kontynuować bez zachowywania odwołań niekolekcjonowanych do teraz zniszczonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="32b43-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="32b43-122">Kto powinien zaimplementować słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="32b43-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="32b43-123">Implementacja niesłabego wzorca zdarzeń jest interesująca głównie dla autorów kontroli.</span><span class="sxs-lookup"><span data-stu-id="32b43-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="32b43-124">Autorem kontrolki jest w dużym stopniu odpowiedzialny za zachowanie i zawieranie kontroli oraz wpływu na aplikacje, w których został wstawiony.</span><span class="sxs-lookup"><span data-stu-id="32b43-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="32b43-125">Obejmuje to zachowanie okresu istnienia obiektu sterowania, w szczególności obsługę opisanego problemu przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="32b43-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="32b43-126">Niektóre scenariusze polegają na wykorzystaniu samego wzorca zdarzenia słabego.</span><span class="sxs-lookup"><span data-stu-id="32b43-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="32b43-127">Jeden taki scenariusz to powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="32b43-127">One such scenario is data binding.</span></span> <span data-ttu-id="32b43-128">W powiązaniu danych wspólne jest, aby obiekt źródłowy był całkowicie niezależny od obiektu odbiornika, który jest obiektem docelowym powiązania.</span><span class="sxs-lookup"><span data-stu-id="32b43-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="32b43-129">Wiele aspektów powiązania danych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] już ma słaby wzorzec zdarzeń stosowany w sposobie implementacji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="32b43-130">Jak zaimplementować wzorzec słabych zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="32b43-131">Istnieją trzy sposoby implementacji słabego wzorca zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="32b43-132">W poniższej tabeli wymieniono trzy podejścia i przedstawiono wskazówki dotyczące sytuacji, w których należy użyć każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="32b43-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="32b43-133">Podejście</span><span class="sxs-lookup"><span data-stu-id="32b43-133">Approach</span></span>|<span data-ttu-id="32b43-134">Kiedy należy zaimplementować</span><span class="sxs-lookup"><span data-stu-id="32b43-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="32b43-135">Użyj istniejącej klasy słabego Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="32b43-136">Jeśli zdarzenie, które chcesz subskrybować, ma odpowiednie <xref:System.Windows.WeakEventManager>, użyj istniejącego słabego Menedżera zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="32b43-137">Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w klasie <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="32b43-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="32b43-138">Ze względu na to, że wliczone Menedżery zdarzeń słabych są ograniczone, prawdopodobnie trzeba będzie wybrać jedną z innych metod.</span><span class="sxs-lookup"><span data-stu-id="32b43-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="32b43-139">Użyj generycznej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="32b43-140">Użyj ogólnego <xref:System.Windows.WeakEventManager%602>, gdy istniejąca <xref:System.Windows.WeakEventManager> jest niedostępna, chcesz ułatwić wdrożenie i nie ma żadnych działań w zakresie wydajności.</span><span class="sxs-lookup"><span data-stu-id="32b43-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="32b43-141">Ogólny <xref:System.Windows.WeakEventManager%602> jest mniej wydajny niż istniejący lub niestandardowy słaby Menedżer zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="32b43-142">Na przykład Klasa generyczna wykonuje więcej odbicia w celu odnalezienia zdarzenia uwzględniającego nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="32b43-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="32b43-143">Ponadto kod, aby zarejestrować zdarzenie przy użyciu ogólnego <xref:System.Windows.WeakEventManager%602>, jest bardziej pełny niż przy użyciu istniejącego lub niestandardowego <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="32b43-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="32b43-144">Utwórz niestandardową klasę słabego Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="32b43-145">Utwórz niestandardową <xref:System.Windows.WeakEventManager>, gdy istniejąca <xref:System.Windows.WeakEventManager> będzie niedostępna, a chcesz uzyskać najlepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="32b43-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="32b43-146">Użycie <xref:System.Windows.WeakEventManager> niestandardowego do subskrybowania zdarzenia będzie bardziej wydajne, ale powiąże się to z kosztem napisania większej ilości kodu na początku.</span><span class="sxs-lookup"><span data-stu-id="32b43-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="32b43-147">Korzystanie z niesłabego Menedżera zdarzeń innej firmy</span><span class="sxs-lookup"><span data-stu-id="32b43-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="32b43-148">Pakiet NuGet ma [kilku słabych menedżerów zdarzeń](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) , a wiele struktur WPF obsługuje również wzorzec (na przykład zobacz [dokumentację biblioteki Prism na temat luźno powiązanej subskrypcji zdarzeń](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="32b43-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="32b43-149">W poniższych sekcjach opisano sposób implementacji słabego wzorca zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="32b43-150">Na potrzeby tej dyskusji wydarzenie subskrybowane ma następujące cechy.</span><span class="sxs-lookup"><span data-stu-id="32b43-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="32b43-151">Nazwa zdarzenia to `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="32b43-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="32b43-152">Zdarzenie jest zgłaszane przez klasę `EventSource`.</span><span class="sxs-lookup"><span data-stu-id="32b43-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="32b43-153">Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="32b43-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="32b43-154">Zdarzenie przekazuje parametr typu `SomeEventEventArgs` do programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="32b43-155">Używanie istniejącej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="32b43-156">Znajdź istniejący słaby Menedżer zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="32b43-157">Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w klasie <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="32b43-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="32b43-158">Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="32b43-159">Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="32b43-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="32b43-160">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="32b43-160">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="32b43-161">Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="32b43-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="32b43-162">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="32b43-162">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="32b43-163">Korzystanie z ogólnej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="32b43-164">Użyj klasy generycznej <xref:System.Windows.WeakEventManager%602> zamiast normalnej podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="32b43-165">W przypadku używania <xref:System.Windows.WeakEventManager%602> do rejestrowania detektorów zdarzeń należy podać Źródło zdarzenia i typ <xref:System.EventArgs> jako parametry typu klasy i wywołania <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="32b43-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="32b43-166">Tworzenie niestandardowej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="32b43-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="32b43-167">Skopiuj następujący szablon klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="32b43-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="32b43-168">Ta klasa dziedziczy z klasy <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="32b43-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="32b43-169">Zastąp nazwę `SomeEventWeakEventManager` własną nazwą.</span><span class="sxs-lookup"><span data-stu-id="32b43-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="32b43-170">Zastąp trzy nazwy opisane wcześniej odpowiednimi nazwami dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="32b43-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="32b43-171">(`SomeEvent`, `EventSource`i `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="32b43-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="32b43-172">Ustaw widoczność (Public/Internal/Private) słabej klasy Menedżera zdarzeń w taki sam sposób jak zdarzenie, które zarządza.</span><span class="sxs-lookup"><span data-stu-id="32b43-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="32b43-173">Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="32b43-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="32b43-174">Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="32b43-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="32b43-175">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="32b43-175">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="32b43-176">Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="32b43-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="32b43-177">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="32b43-177">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="32b43-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="32b43-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="32b43-179">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="32b43-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="32b43-180">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="32b43-180">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
