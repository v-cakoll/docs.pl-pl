---
title: Projekt zdarzenia
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: b44ee5933f8629b4dddbf3be1b79b2e77b0254f7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741687"
---
# <a name="event-design"></a><span data-ttu-id="f9b64-102">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f9b64-102">Event Design</span></span>
<span data-ttu-id="f9b64-103">Zdarzenia są najczęściej używane w formie wywołań zwrotnych (konstrukcje, które umożliwiają platformie Wywoływanie kodu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="f9b64-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="f9b64-104">Inne mechanizmy wywołania zwrotnego obejmują członków, którzy korzystają z delegatów, wirtualnych elementów członkowskich i wtyczek opartych na interfejsie. dane z badań użyteczności wskazują, że większość deweloperów jest bardziej wygodna przy użyciu zdarzeń, niż korzystają z innych mechanizmów wywołania zwrotnego .</span><span class="sxs-lookup"><span data-stu-id="f9b64-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="f9b64-105">Zdarzenia są dobrze zintegrowane z programem Visual Studio i wieloma językami.</span><span class="sxs-lookup"><span data-stu-id="f9b64-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="f9b64-106">Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed zmianą systemu, zwane przed zdarzeniami i zdarzenia zgłoszone po zmianie stanu, nazywanego po wprowadzeniu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="f9b64-107">Przykładem przedevent może być `Form.Closing`, który jest wywoływany przed zamknięciem formularza.</span><span class="sxs-lookup"><span data-stu-id="f9b64-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="f9b64-108">Przykładem zdarzenia po zdarzeniu może być `Form.Closed`, które jest wywoływane po zamknięciu formularza.</span><span class="sxs-lookup"><span data-stu-id="f9b64-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="f9b64-109">✔️ należy używać terminu "Zgłoś" dla zdarzeń, a nie "ognia" lub "wyzwalacza".</span><span class="sxs-lookup"><span data-stu-id="f9b64-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="f9b64-110">✔️ używać <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="f9b64-111">✔️ ROZWAŻYĆ użycie podklasy <xref:System.EventArgs> jako argumentu zdarzenia, o ile nie masz absolutnej pewności, że zdarzenie nigdy nie będzie wymagało przeprowadzenia jakichkolwiek danych do metody obsługi zdarzeń, w takim przypadku można użyć typu `EventArgs` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f9b64-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="f9b64-112">W przypadku dostarczania interfejsu API za pomocą `EventArgs` bezpośrednio nie będzie można dodawać żadnych danych, które mają być przenoszone ze zdarzeniem bez przerywania zgodności.</span><span class="sxs-lookup"><span data-stu-id="f9b64-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="f9b64-113">Jeśli używasz podklasy, nawet jeśli początkowo całkowicie jest pusta, możesz w razie potrzeby dodać właściwości do podklasy.</span><span class="sxs-lookup"><span data-stu-id="f9b64-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="f9b64-114">Aby zgłosić każde zdarzenie, ✔️ użyj chronionej metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="f9b64-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="f9b64-115">Ma to zastosowanie tylko do zdarzeń niestatycznych dla niezapieczętowanych klas, nie do struktur, klas zapieczętowanych lub zdarzeń statycznych.</span><span class="sxs-lookup"><span data-stu-id="f9b64-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="f9b64-116">Celem metody jest zapewnienie metodu do obsługi zdarzenia przy użyciu przesłonięcia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="f9b64-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="f9b64-117">Zastępowanie jest bardziej elastyczne, szybsze i bardziej naturalne w przypadku obsługi zdarzeń klasy podstawowej w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f9b64-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="f9b64-118">Według Konwencji, nazwa metody powinna zaczynać się od "on" i następować nazwą zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9b64-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="f9b64-119">Klasa pochodna może zrezygnować z implementacji podstawowej metody w jej zastępowaniu.</span><span class="sxs-lookup"><span data-stu-id="f9b64-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="f9b64-120">Przygotowuje się do tego przez nie uwzględniając żadnego przetwarzania w metodzie, która jest wymagana do poprawnego działania klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="f9b64-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="f9b64-121">✔️ przyjmuje jeden parametr do metody chronionej, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f9b64-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="f9b64-122">Parametr powinien mieć nazwę `e` i powinien być typem klasy argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9b64-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="f9b64-123">❌ nie przekazywać wartości null jako nadawcy podczas podnoszenia niestatycznego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9b64-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="f9b64-124">✔️ przekazywać wartości null jako nadawcy podczas podnoszenia zdarzenia statycznego.</span><span class="sxs-lookup"><span data-stu-id="f9b64-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="f9b64-125">❌ nie przekazywać wartości null jako parametru danych zdarzenia podczas podnoszenia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f9b64-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="f9b64-126">Należy przekazać `EventArgs.Empty`, jeśli nie chcesz przekazać żadnych danych do metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="f9b64-127">Deweloperzy oczekują, że ten parametr nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="f9b64-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="f9b64-128">✔️ ROZWAŻYĆ podnoszenie poziomu zdarzeń, które użytkownik końcowy może anulować.</span><span class="sxs-lookup"><span data-stu-id="f9b64-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="f9b64-129">Dotyczy to przede wszystkim zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="f9b64-130">Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> lub jej podklasy jako argumentu zdarzenia, aby umożliwić użytkownikowi końcowemu anulowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="f9b64-131">Projekt programu obsługi zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="f9b64-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="f9b64-132">Istnieją przypadki, w których nie można użyć `EventHandler<T>`, na przykład gdy struktura musi działać we wcześniejszych wersjach środowiska CLR, które nie obsługują typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="f9b64-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="f9b64-133">W takich przypadkach może być konieczne zaprojektowanie i opracowanie niestandardowego delegata obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="f9b64-134">✔️ używać zwracanego typu void dla programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="f9b64-135">Procedura obsługi zdarzeń może wywoływać wiele metod obsługi zdarzeń, prawdopodobnie na wielu obiektach.</span><span class="sxs-lookup"><span data-stu-id="f9b64-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="f9b64-136">Jeśli metody obsługi zdarzeń mogły zwrócić wartość, dla każdego wywołania zdarzenia może istnieć wiele wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="f9b64-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="f9b64-137">✔️ używać `object` jako typu pierwszego parametru programu obsługi zdarzeń i wywoływać `sender`.</span><span class="sxs-lookup"><span data-stu-id="f9b64-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="f9b64-138">✔️ używać <xref:System.EventArgs?displayProperty=nameWithType> lub jego podklasy jako typu drugiego parametru programu obsługi zdarzeń i wywoływać `e`.</span><span class="sxs-lookup"><span data-stu-id="f9b64-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="f9b64-139">❌ nie mają więcej niż dwóch parametrów dla programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9b64-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="f9b64-140">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="f9b64-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f9b64-141">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="f9b64-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f9b64-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9b64-142">See also</span></span>

- [<span data-ttu-id="f9b64-143">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f9b64-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="f9b64-144">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="f9b64-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
