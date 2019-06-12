---
title: Słabe wzorce zdarzeń
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 0c5bae64fbbeddedd905e5df0b5789542e29f2f1
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833935"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="993e6-102">Słabe wzorce zdarzeń</span><span class="sxs-lookup"><span data-stu-id="993e6-102">Weak Event Patterns</span></span>
<span data-ttu-id="993e6-103">W przypadku aplikacji jest możliwe, że programy obsługi, które są dołączone do źródła zdarzeń, nie jest niszczony w połączeniu z obiekt odbiornik, który jest dołączony program obsługi do źródła.</span><span class="sxs-lookup"><span data-stu-id="993e6-103">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="993e6-104">Taka sytuacja może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="993e6-104">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="993e6-105">wprowadzono szablon projektu, który może służyć do rozwiązania tego problemu, przesyłając klasy Menedżera dedykowane dla określonych zdarzeń i implementowania interfejsu na odbiorniki dla tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-105">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="993e6-106">Ten wzorzec projektowy jest znany jako *słaby wzorzec zdarzeń*.</span><span class="sxs-lookup"><span data-stu-id="993e6-106">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="993e6-107">Dlaczego warto wdrażać słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="993e6-107">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="993e6-108">Nasłuchiwanie zdarzeń może prowadzić do przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="993e6-108">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="993e6-109">Typowych technik w celu nasłuchiwania na zdarzenie jest należy użyć składni specyficzny dla języka, który dołącza obsługę do zdarzenia w źródle.</span><span class="sxs-lookup"><span data-stu-id="993e6-109">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="993e6-110">Na przykład w C#, czy składnia jest: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span><span class="sxs-lookup"><span data-stu-id="993e6-110">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="993e6-111">Ta metoda tworzy silne odwołanie ze źródła zdarzeń do odbiornika zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-111">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="993e6-112">Zazwyczaj Dołączanie programu obsługi zdarzeń dla odbiornika powoduje, że odbiornika mieć okresu istnienia obiektu, który ma wpływ okres istnienia obiektu źródłowego (chyba że program obsługi zdarzeń jest jawnie usunięte).</span><span class="sxs-lookup"><span data-stu-id="993e6-112">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="993e6-113">Jednak w pewnych okolicznościach może być okres istnienia obiektu nasłuchującego kontrolowany przez inne czynniki, takie jak aktualnie przynależność do drzewa wizualnego w aplikacji, a nie przez okres istnienia źródła.</span><span class="sxs-lookup"><span data-stu-id="993e6-113">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="993e6-114">Po każdym okresie istnienia obiektu źródłowego wykracza poza okres istnienia obiektu odbiornika, wzorzec zdarzeń normalne prowadzi do przeciek pamięci: odbiornika jest życiu dłużej, niż planowano.</span><span class="sxs-lookup"><span data-stu-id="993e6-114">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="993e6-115">Słaby wzorzec zdarzeń zaprojektowano w celu rozwiązania tego problemu przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="993e6-115">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="993e6-116">Słaby wzorzec zdarzeń można zawsze wtedy, gdy odbiornik musi zarejestrować zdarzenie, ale odbiornik nie jawnie wiedział, kiedy można wyrejestrować.</span><span class="sxs-lookup"><span data-stu-id="993e6-116">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="993e6-117">Słaby wzorzec zdarzeń można również zawsze wtedy, gdy okres istnienia obiektu źródła przekracza okres istnienia obiektu przydatne odbiornika.</span><span class="sxs-lookup"><span data-stu-id="993e6-117">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="993e6-118">(W tym przypadku *przydatne* jest określany przez użytkownika.) Słaby wzorzec zdarzeń umożliwia odbiornika przeprowadzać rejestrację i otrzymają zdarzenie bez wywierania wpływu na właściwości okresu istnienia obiektu odbiornika w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="993e6-118">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="993e6-119">W efekcie odwołanie domniemane ze źródła nie określa, czy odbiornik kwalifikują się do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="993e6-119">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="993e6-120">Odwołanie jest słabe odwołanie, w związku z tym nazewnictwa słaby wzorzec zdarzeń i powiązane [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="993e6-120">The reference is a weak reference, thus the naming of the weak event pattern and the related [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)].</span></span> <span data-ttu-id="993e6-121">Odbiornik może zostać usunięte zebrane lub w przeciwnym razie zniszczenia obiektu, a źródła można kontynuować bez zachowania noncollectible obsługi odwołań do obiektu teraz niszczone.</span><span class="sxs-lookup"><span data-stu-id="993e6-121">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="993e6-122">Kto należy zaimplementować słaby wzorzec zdarzeń?</span><span class="sxs-lookup"><span data-stu-id="993e6-122">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="993e6-123">Implementacja wzorca zdarzeń słabych jest interesująca przede wszystkim dla autorów kontroli.</span><span class="sxs-lookup"><span data-stu-id="993e6-123">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="993e6-124">Jako autor kontroli odpowiedzialność za stopniu zachowanie i zawierania kontroli nad oraz wpływ, znajdującymi się na aplikacjach, w których zostanie ona wstawiona.</span><span class="sxs-lookup"><span data-stu-id="993e6-124">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="993e6-125">W tym kontroli zachowania okresu istnienia obiektu, w szczególności obsługi problem przeciek pamięci opisem.</span><span class="sxs-lookup"><span data-stu-id="993e6-125">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="993e6-126">Niektóre scenariusze natury nadają się do aplikacji słaby wzorzec zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-126">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="993e6-127">Taki scenariusz jest powiązanie danych.</span><span class="sxs-lookup"><span data-stu-id="993e6-127">One such scenario is data binding.</span></span> <span data-ttu-id="993e6-128">W powiązaniu danych to częsty problem w obiekcie źródłowym w celu całkowicie niezależne od obiektu odbiornika, który jest elementem docelowym powiązania.</span><span class="sxs-lookup"><span data-stu-id="993e6-128">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="993e6-129">Wiele aspektów [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] już powiązania danych mają słaby wzorzec zdarzeń stosowane w implementacji zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-129">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="993e6-130">Jak zaimplementować słaby wzorzec zdarzeń</span><span class="sxs-lookup"><span data-stu-id="993e6-130">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="993e6-131">Istnieją trzy sposoby, aby zaimplementować słaby wzorzec zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-131">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="993e6-132">Poniższa tabela zawiera trzy metody oraz zawiera pewne wskazówki dotyczące kiedy należy używać każdego.</span><span class="sxs-lookup"><span data-stu-id="993e6-132">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="993e6-133">Podejście</span><span class="sxs-lookup"><span data-stu-id="993e6-133">Approach</span></span>|<span data-ttu-id="993e6-134">O czasie implementacji</span><span class="sxs-lookup"><span data-stu-id="993e6-134">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="993e6-135">Użyj istniejącej klasy menedżera zdarzeń słabych</span><span class="sxs-lookup"><span data-stu-id="993e6-135">Use an existing weak event manager class</span></span>|<span data-ttu-id="993e6-136">Jeśli zdarzenie, aby subskrybować ma odpowiadające mu <xref:System.Windows.WeakEventManager>, przy użyciu istniejącego menedżera zdarzeń słabych.</span><span class="sxs-lookup"><span data-stu-id="993e6-136">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="993e6-137">Listę menedżerów zdarzeń słabych, które są uwzględniane przy użyciu platformy WPF, na ten temat można znaleźć w hierarchii dziedziczenia w <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="993e6-137">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="993e6-138">Ponieważ menedżerów zdarzeń słabych uwzględniane są ograniczone, prawdopodobnie musisz wybrać jedną z innych metod.</span><span class="sxs-lookup"><span data-stu-id="993e6-138">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="993e6-139">Używanie klasy menedżera zdarzeń słabych generycznych</span><span class="sxs-lookup"><span data-stu-id="993e6-139">Use a generic weak event manager class</span></span>|<span data-ttu-id="993e6-140">Korzystają z ogólnego <xref:System.Windows.WeakEventManager%602> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępny, chcesz, aby łatwo wdrożyć, a nie są faktycznie zajmuje się wydajność.</span><span class="sxs-lookup"><span data-stu-id="993e6-140">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="993e6-141">Ogólny <xref:System.Windows.WeakEventManager%602> jest mniej wydajne niż do istniejącego lub niestandardowego Menedżera zdarzeń słabych.</span><span class="sxs-lookup"><span data-stu-id="993e6-141">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="993e6-142">Na przykład klasy generycznej jest więcej odbicia, aby odnaleźć zdarzenie otrzymuje nazwę zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-142">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="993e6-143">Ponadto kod, aby rejestrować zdarzenia za pomocą ogólnego <xref:System.Windows.WeakEventManager%602> jest bardziej pełne niż korzystanie z istniejących lub niestandardowych <xref:System.Windows.WeakEventManager>.</span><span class="sxs-lookup"><span data-stu-id="993e6-143">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="993e6-144">Utwórz klasę Menedżera niestandardowych zdarzeń słabych</span><span class="sxs-lookup"><span data-stu-id="993e6-144">Create a custom weak event manager class</span></span>|<span data-ttu-id="993e6-145">Utwórz niestandardową <xref:System.Windows.WeakEventManager> kiedy istniejący <xref:System.Windows.WeakEventManager> nie jest dostępna i uzyskania najlepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="993e6-145">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="993e6-146">Za pomocą niestandardowego <xref:System.Windows.WeakEventManager> do subskrybowania zdarzenia będzie bardziej wydajne, ale wiąże się koszt pisania więcej kodu na początku.</span><span class="sxs-lookup"><span data-stu-id="993e6-146">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="993e6-147">Korzystanie z Menedżera zdarzeń słabych innych firm</span><span class="sxs-lookup"><span data-stu-id="993e6-147">Use a third-party weak event manager</span></span>|<span data-ttu-id="993e6-148">NuGet ma [kilka zdarzeń słabych menedżerów](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) i wiele struktur WPF obsługuje również wzorca (na przykład zobacz [firmy pryzmat dokumentację dotyczącą subskrypcji luźno powiązanych zdarzeń](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span><span class="sxs-lookup"><span data-stu-id="993e6-148">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="993e6-149">Poniżej opisano sposób implementacji słaby wzorzec zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-149">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="993e6-150">Dla celów tej dyskusji zdarzenia, aby zasubskrybować ma następujące cechy.</span><span class="sxs-lookup"><span data-stu-id="993e6-150">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="993e6-151">Nazwa zdarzenia jest `SomeEvent`.</span><span class="sxs-lookup"><span data-stu-id="993e6-151">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="993e6-152">Zdarzenie jest wywoływane przez `EventSource` klasy.</span><span class="sxs-lookup"><span data-stu-id="993e6-152">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="993e6-153">Program obsługi zdarzeń ma typ: `SomeEventEventHandler` (lub `EventHandler<SomeEventEventArgs>`).</span><span class="sxs-lookup"><span data-stu-id="993e6-153">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="993e6-154">Zdarzenie przekazuje parametr typu `SomeEventEventArgs` do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="993e6-154">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="993e6-155">Przy użyciu istniejącej klasy Menedżer zdarzeń słabych</span><span class="sxs-lookup"><span data-stu-id="993e6-155">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="993e6-156">Znajdowanie istniejącego zdarzenia słabe menedżera.</span><span class="sxs-lookup"><span data-stu-id="993e6-156">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="993e6-157">Listę menedżerów zdarzeń słabych, które są uwzględniane przy użyciu platformy WPF, na ten temat można znaleźć w hierarchii dziedziczenia w <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="993e6-157">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="993e6-158">Użyj nowego menedżera zdarzeń słabych zamiast zaczep zdarzenia normalny.</span><span class="sxs-lookup"><span data-stu-id="993e6-158">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="993e6-159">Na przykład, jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="993e6-159">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="993e6-160">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="993e6-160">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="993e6-161">Podobnie jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="993e6-161">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="993e6-162">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="993e6-162">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="993e6-163">Za pomocą klasy ogólnej słabe Menedżer zdarzeń</span><span class="sxs-lookup"><span data-stu-id="993e6-163">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="993e6-164">Używać ogólnych <xref:System.Windows.WeakEventManager%602> klasy zamiast zaczep zdarzenia normalny.</span><span class="sxs-lookup"><span data-stu-id="993e6-164">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="993e6-165">Kiedy używać <xref:System.Windows.WeakEventManager%602> rejestrowanie detektorów zdarzeń, podaj źródło zdarzenia i <xref:System.EventArgs> typu jako parametrów typu klasy i wywołania <xref:System.Windows.WeakEventManager%602.AddHandler%2A> jak pokazano w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="993e6-165">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="993e6-166">Tworzenie niestandardowych słabe klasy Menedżer zdarzeń</span><span class="sxs-lookup"><span data-stu-id="993e6-166">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="993e6-167">Skopiuj następujący szablon klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="993e6-167">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="993e6-168">Ta klasa dziedziczy <xref:System.Windows.WeakEventManager> klasy.</span><span class="sxs-lookup"><span data-stu-id="993e6-168">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="993e6-169">Zastąp `SomeEventWeakEventManager` nazwa własną nazwą.</span><span class="sxs-lookup"><span data-stu-id="993e6-169">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="993e6-170">Zastąp te trzy nazwy opisane wcześniej przy użyciu odpowiadających im nazw do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="993e6-170">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="993e6-171">(`SomeEvent`, `EventSource`, i `SomeEventEventArgs`)</span><span class="sxs-lookup"><span data-stu-id="993e6-171">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="993e6-172">Ustaw widoczność (publiczne / wewnętrzne / prywatne) klasy menedżera zdarzeń słabych na taką samą widoczność jak zdarzenia, którymi zarządza.</span><span class="sxs-lookup"><span data-stu-id="993e6-172">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="993e6-173">Użyj nowego menedżera zdarzeń słabych zamiast zaczep zdarzenia normalny.</span><span class="sxs-lookup"><span data-stu-id="993e6-173">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="993e6-174">Na przykład, jeśli kod używa następującego wzorca do subskrybowania zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="993e6-174">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="993e6-175">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="993e6-175">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="993e6-176">Podobnie jeśli kod używa następującego wzorca, aby anulować subskrypcję zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="993e6-176">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="993e6-177">Zmień go na następujący wzór:</span><span class="sxs-lookup"><span data-stu-id="993e6-177">Change it to the following pattern:</span></span>  
  
    ```  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="993e6-178">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="993e6-178">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="993e6-179">Przegląd zdarzeń trasowanych</span><span class="sxs-lookup"><span data-stu-id="993e6-179">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="993e6-180">Powiązanie danych — omówienie</span><span class="sxs-lookup"><span data-stu-id="993e6-180">Data Binding Overview</span></span>](../data/data-binding-overview.md)
