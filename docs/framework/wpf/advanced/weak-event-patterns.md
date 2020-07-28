---
title: Słabe wzorce zdarzeń
description: Dowiedz się więcej o Windows Presentation Foundation słabym wzorcu zdarzeń, który rozwiązuje problem niezniszczonych programów obsługi, unikając przecieków pamięci.
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168270"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="73fc3-103">Słabe wzorce zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-103">Weak Event Patterns</span></span>
<span data-ttu-id="73fc3-104">W aplikacjach jest możliwe, że programy obsługi dołączone do źródeł zdarzeń nie zostaną zniszczone w koordynacji z obiektem odbiornika, który dołączył program obsługi do źródła.</span><span class="sxs-lookup"><span data-stu-id="73fc3-104">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="73fc3-105">Ta sytuacja może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="73fc3-105">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="73fc3-106">wprowadza Wzorzec projektowy, który może służyć do rozwiązywania tego problemu, dostarczając dedykowaną klasę Menedżera dla określonych zdarzeń i implementując interfejs w detektorach dla tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73fc3-106">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="73fc3-107">Ten Wzorzec projektowy jest znany jako *słaby wzorzec zdarzeń*.</span><span class="sxs-lookup"><span data-stu-id="73fc3-107">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="73fc3-108">Dlaczego warto zaimplementować słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="73fc3-108">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="73fc3-109">Nasłuchiwanie zdarzeń może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="73fc3-109">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="73fc3-110">Typową techniką nasłuchiwania zdarzeń jest użycie składni charakterystycznej dla języka, która dołącza procedurę obsługi do zdarzenia w źródle.</span><span class="sxs-lookup"><span data-stu-id="73fc3-110">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="73fc3-111">Na przykład w języku C# składnia jest następująca: `source.SomeEvent += new SomeEventHandler(MyEventHandler)` .</span><span class="sxs-lookup"><span data-stu-id="73fc3-111">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="73fc3-112">Ta technika tworzy silne odwołanie ze źródła zdarzenia do odbiornika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-112">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="73fc3-113">Zwykle dołączenie obsługi zdarzeń dla odbiornika powoduje, że odbiornik ma czas istnienia obiektu, na który ma wpływ okres istnienia obiektu (chyba że program obsługi zdarzeń został jawnie usunięty).</span><span class="sxs-lookup"><span data-stu-id="73fc3-113">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="73fc3-114">W pewnych okolicznościach może być konieczne, aby okres istnienia obiektu odbiornika był kontrolowany przez inne czynniki, na przykład czy należy on do drzewa wizualnego aplikacji, a nie przez okres istnienia źródła.</span><span class="sxs-lookup"><span data-stu-id="73fc3-114">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="73fc3-115">Za każdym razem, gdy okres istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, normalny wzorzec zdarzenia prowadzi do przecieku pamięci: odbiornik działa dłużej niż zamierzone.</span><span class="sxs-lookup"><span data-stu-id="73fc3-115">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="73fc3-116">Niesłaby wzorzec zdarzeń został zaprojektowany w celu rozwiązania tego problemu przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="73fc3-116">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="73fc3-117">Wzorca zdarzeń słabych można użyć zawsze, gdy odbiornik musi zarejestrować się na potrzeby zdarzenia, ale odbiornik nie wie jawnie, kiedy należy wyrejestrować.</span><span class="sxs-lookup"><span data-stu-id="73fc3-117">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="73fc3-118">Wzorca zdarzeń słabych można również użyć zawsze, gdy okres istnienia obiektu źródła przekracza użyteczny okres istnienia odbiornika.</span><span class="sxs-lookup"><span data-stu-id="73fc3-118">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="73fc3-119">(W tym przypadku jest to *przydatne* przez użytkownika). Słaby wzorzec zdarzeń umożliwia odbiornikowi rejestrowanie i odbieranie zdarzenia bez wpływu na charakterystykę okresu istnienia obiektu odbiornika w jakikolwiek sposób.</span><span class="sxs-lookup"><span data-stu-id="73fc3-119">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="73fc3-120">W efekcie odwołanie implikowane ze źródła nie określa, czy odbiornik kwalifikuje się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="73fc3-120">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="73fc3-121">Odwołanie to słabe odwołanie, w związku z czym nazwa słabego wzorca zdarzeń i powiązane interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="73fc3-121">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="73fc3-122">Odbiornik może być wyrzucony lub zniszczony w inny sposób, a źródło może kontynuować bez zachowywania odwołań niekolekcjonowanych do teraz zniszczonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="73fc3-122">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="73fc3-123">Kto powinien zaimplementować słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="73fc3-123">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="73fc3-124">Implementacja niesłabego wzorca zdarzeń jest interesująca głównie dla autorów kontroli.</span><span class="sxs-lookup"><span data-stu-id="73fc3-124">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="73fc3-125">Autorem kontrolki jest w dużym stopniu odpowiedzialny za zachowanie i zawieranie kontroli oraz wpływu na aplikacje, w których został wstawiony.</span><span class="sxs-lookup"><span data-stu-id="73fc3-125">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="73fc3-126">Obejmuje to zachowanie okresu istnienia obiektu sterowania, w szczególności obsługę opisanego problemu przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="73fc3-126">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="73fc3-127">Niektóre scenariusze polegają na wykorzystaniu samego wzorca zdarzenia słabego.</span><span class="sxs-lookup"><span data-stu-id="73fc3-127">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="73fc3-128">Jeden taki scenariusz to powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="73fc3-128">One such scenario is data binding.</span></span> <span data-ttu-id="73fc3-129">W powiązaniu danych wspólne jest, aby obiekt źródłowy był całkowicie niezależny od obiektu odbiornika, który jest obiektem docelowym powiązania.</span><span class="sxs-lookup"><span data-stu-id="73fc3-129">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="73fc3-130">Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] powiązania danych ma już niesłaby wzorzec zdarzeń stosowany w sposobie implementacji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-130">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="73fc3-131">Jak zaimplementować wzorzec słabych zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-131">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="73fc3-132">Istnieją trzy sposoby implementacji słabego wzorca zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-132">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="73fc3-133">W poniższej tabeli wymieniono trzy podejścia i przedstawiono wskazówki dotyczące sytuacji, w których należy użyć każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="73fc3-133">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="73fc3-134">Podejście</span><span class="sxs-lookup"><span data-stu-id="73fc3-134">Approach</span></span>|<span data-ttu-id="73fc3-135">Kiedy należy zaimplementować</span><span class="sxs-lookup"><span data-stu-id="73fc3-135">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="73fc3-136">Użyj istniejącej klasy słabego Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-136">Use an existing weak event manager class</span></span>|<span data-ttu-id="73fc3-137">Jeśli zdarzenie, które chcesz subskrybować, ma odpowiednie <xref:System.Windows.WeakEventManager> użycie, użyj istniejącego słabego Menedżera zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-137">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="73fc3-138">Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w <xref:System.Windows.WeakEventManager> klasie.</span><span class="sxs-lookup"><span data-stu-id="73fc3-138">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="73fc3-139">Ze względu na to, że wliczone Menedżery zdarzeń słabych są ograniczone, prawdopodobnie trzeba będzie wybrać jedną z innych metod.</span><span class="sxs-lookup"><span data-stu-id="73fc3-139">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="73fc3-140">Użyj generycznej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-140">Use a generic weak event manager class</span></span>|<span data-ttu-id="73fc3-141">Użyj generycznej <xref:System.Windows.WeakEventManager%602> , gdy istniejąca <xref:System.Windows.WeakEventManager> jest niedostępna, chcesz ułatwić wdrożenie i nie ma żadnych informacji o wydajności.</span><span class="sxs-lookup"><span data-stu-id="73fc3-141">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="73fc3-142">Wartość ogólna <xref:System.Windows.WeakEventManager%602> jest mniej wydajna niż istniejący lub niestandardowy słaby Menedżer zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-142">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="73fc3-143">Na przykład Klasa generyczna wykonuje więcej odbicia w celu odnalezienia zdarzenia uwzględniającego nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73fc3-143">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="73fc3-144">Ponadto kod, aby zarejestrować zdarzenie przy użyciu generycznego, <xref:System.Windows.WeakEventManager%602> jest bardziej pełny niż użycie istniejącej lub niestandardowej <xref:System.Windows.WeakEventManager> .</span><span class="sxs-lookup"><span data-stu-id="73fc3-144">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="73fc3-145">Utwórz niestandardową klasę słabego Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-145">Create a custom weak event manager class</span></span>|<span data-ttu-id="73fc3-146">Utwórz niestandardową, <xref:System.Windows.WeakEventManager> gdy istniejąca <xref:System.Windows.WeakEventManager> jest niedostępna, i potrzebujesz najlepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="73fc3-146">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="73fc3-147">Użycie niestandardowego <xref:System.Windows.WeakEventManager> do subskrybowania zdarzenia będzie bardziej wydajne, ale powiąże się to z kosztem napisania większej ilości kodu na początku.</span><span class="sxs-lookup"><span data-stu-id="73fc3-147">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="73fc3-148">Korzystanie z niesłabego Menedżera zdarzeń innej firmy</span><span class="sxs-lookup"><span data-stu-id="73fc3-148">Use a third-party weak event manager</span></span>|<span data-ttu-id="73fc3-149">Pakiet NuGet ma [kilku słabych menedżerów zdarzeń](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) , a wiele struktur WPF obsługuje również wzorzec (na przykład zobacz [dokumentację biblioteki Prism na temat luźno powiązanej subskrypcji zdarzeń](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="73fc3-149">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="73fc3-150">W poniższych sekcjach opisano sposób implementacji słabego wzorca zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-150">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="73fc3-151">Na potrzeby tej dyskusji wydarzenie subskrybowane ma następujące cechy.</span><span class="sxs-lookup"><span data-stu-id="73fc3-151">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="73fc3-152">Nazwa zdarzenia to `SomeEvent` .</span><span class="sxs-lookup"><span data-stu-id="73fc3-152">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="73fc3-153">Zdarzenie jest zgłaszane przez `EventSource` klasę.</span><span class="sxs-lookup"><span data-stu-id="73fc3-153">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="73fc3-154">Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>` ).</span><span class="sxs-lookup"><span data-stu-id="73fc3-154">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="73fc3-155">Zdarzenie przekazuje parametr typu `SomeEventEventArgs` do programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-155">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="73fc3-156">Używanie istniejącej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-156">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="73fc3-157">Znajdź istniejący słaby Menedżer zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-157">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="73fc3-158">Aby zapoznać się z listą słabych menedżerów zdarzeń, które są dołączone do platformy WPF, zobacz Hierarchia dziedziczenia w <xref:System.Windows.WeakEventManager> klasie.</span><span class="sxs-lookup"><span data-stu-id="73fc3-158">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="73fc3-159">Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-159">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="73fc3-160">Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="73fc3-160">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="73fc3-161">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="73fc3-161">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="73fc3-162">Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="73fc3-162">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="73fc3-163">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="73fc3-163">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="73fc3-164">Korzystanie z ogólnej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-164">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="73fc3-165">Użyj klasy generycznej <xref:System.Windows.WeakEventManager%602> zamiast normalnej podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-165">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="73fc3-166">W przypadku korzystania <xref:System.Windows.WeakEventManager%602> z programu do rejestrowania detektorów zdarzeń należy podać Źródło zdarzenia i <xref:System.EventArgs> Typ jako parametry typu klasy i wywołania, <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="73fc3-166">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="73fc3-167">Tworzenie niestandardowej słabej klasy Menedżera zdarzeń</span><span class="sxs-lookup"><span data-stu-id="73fc3-167">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="73fc3-168">Skopiuj następujący szablon klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="73fc3-168">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="73fc3-169">Ta klasa dziedziczy z <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="73fc3-169">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="73fc3-170">Zastąp `SomeEventWeakEventManager` nazwę własną nazwą.</span><span class="sxs-lookup"><span data-stu-id="73fc3-170">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="73fc3-171">Zastąp trzy nazwy opisane wcześniej odpowiednimi nazwami dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73fc3-171">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="73fc3-172">( `SomeEvent` , `EventSource` i `SomeEventEventArgs` )</span><span class="sxs-lookup"><span data-stu-id="73fc3-172">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="73fc3-173">Ustaw widoczność (Public/Internal/Private) słabej klasy Menedżera zdarzeń w taki sam sposób jak zdarzenie, które zarządza.</span><span class="sxs-lookup"><span data-stu-id="73fc3-173">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="73fc3-174">Użyj nowego słabego Menedżera zdarzeń zamiast normalnego podłączenie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="73fc3-174">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="73fc3-175">Na przykład jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="73fc3-175">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="73fc3-176">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="73fc3-176">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="73fc3-177">Podobnie, jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="73fc3-177">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="73fc3-178">Zmień go na następujący wzorzec:</span><span class="sxs-lookup"><span data-stu-id="73fc3-178">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="73fc3-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73fc3-179">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="73fc3-180">Przegląd Zdarzenia trasowane</span><span class="sxs-lookup"><span data-stu-id="73fc3-180">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="73fc3-181">Przegląd powiązań danych</span><span class="sxs-lookup"><span data-stu-id="73fc3-181">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
