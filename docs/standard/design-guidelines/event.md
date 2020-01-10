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
ms.openlocfilehash: 78d765a7af77b1e6a6ecd483677cea2d4c6b0d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709429"
---
# <a name="event-design"></a><span data-ttu-id="d5736-102">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d5736-102">Event Design</span></span>
<span data-ttu-id="d5736-103">Zdarzenia są najczęściej używane w formie wywołań zwrotnych (konstrukcje, które umożliwiają platformie Wywoływanie kodu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="d5736-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="d5736-104">Inne mechanizmy wywołania zwrotnego obejmują członków, którzy korzystają z delegatów, wirtualnych elementów członkowskich i wtyczek opartych na interfejsie. dane z badań użyteczności wskazują, że większość deweloperów jest bardziej wygodna przy użyciu zdarzeń, niż korzystają z innych mechanizmów wywołania zwrotnego .</span><span class="sxs-lookup"><span data-stu-id="d5736-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="d5736-105">Zdarzenia są dobrze zintegrowane z programem Visual Studio i wieloma językami.</span><span class="sxs-lookup"><span data-stu-id="d5736-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="d5736-106">Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed zmianą systemu, zwane przed zdarzeniami i zdarzenia zgłoszone po zmianie stanu, nazywanego po wprowadzeniu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="d5736-107">Przykładem przedevent może być `Form.Closing`, który jest wywoływany przed zamknięciem formularza.</span><span class="sxs-lookup"><span data-stu-id="d5736-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="d5736-108">Przykładem zdarzenia po zdarzeniu może być `Form.Closed`, które jest wywoływane po zamknięciu formularza.</span><span class="sxs-lookup"><span data-stu-id="d5736-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="d5736-109">**✓ DO** używany jest termin "raise" dla zdarzenia, a nie "fire" lub "wyzwolenia".</span><span class="sxs-lookup"><span data-stu-id="d5736-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="d5736-110">**✓ DO** użyj <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="d5736-111">**✓ CONSIDER** przy użyciu podklasą <xref:System.EventArgs> jako argument zdarzenia, jeśli nie masz pewności absolutnie zdarzenie nie będzie trzeba do przenoszenia danych do obsługi metody zdarzeń w takim przypadku można zastosować `EventArgs` wpisać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="d5736-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="d5736-112">W przypadku dostarczania interfejsu API za pomocą `EventArgs` bezpośrednio nie będzie można dodawać żadnych danych, które mają być przenoszone ze zdarzeniem bez przerywania zgodności.</span><span class="sxs-lookup"><span data-stu-id="d5736-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="d5736-113">Jeśli używasz podklasy, nawet jeśli początkowo całkowicie jest pusta, możesz w razie potrzeby dodać właściwości do podklasy.</span><span class="sxs-lookup"><span data-stu-id="d5736-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="d5736-114">**✓ DO** Użyj chronione metody wirtualnej, aby wywołać każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5736-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="d5736-115">Ma to zastosowanie tylko do zdarzeń niestatycznych dla niezapieczętowanych klas, nie do struktur, klas zapieczętowanych lub zdarzeń statycznych.</span><span class="sxs-lookup"><span data-stu-id="d5736-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="d5736-116">Celem metody jest zapewnienie metodu do obsługi zdarzenia przy użyciu przesłonięcia klasy pochodnej.</span><span class="sxs-lookup"><span data-stu-id="d5736-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="d5736-117">Zastępowanie jest bardziej elastyczne, szybsze i bardziej naturalne w przypadku obsługi zdarzeń klasy podstawowej w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="d5736-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="d5736-118">Według Konwencji, nazwa metody powinna zaczynać się od "on" i następować nazwą zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5736-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="d5736-119">Klasa pochodna może zrezygnować z implementacji podstawowej metody w jej zastępowaniu.</span><span class="sxs-lookup"><span data-stu-id="d5736-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="d5736-120">Przygotowuje się do tego przez nie uwzględniając żadnego przetwarzania w metodzie, która jest wymagana do poprawnego działania klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d5736-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="d5736-121">**✓ DO** przyjmować jeden parametr do metody chronionych, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d5736-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="d5736-122">Parametr powinien mieć nazwę `e` i powinien być typem klasy argumentu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5736-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="d5736-123">**X DO NOT** należy przekazać wartość null jako nadawcę podczas wywołaniem Niestatyczne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5736-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="d5736-124">**✓ DO** przekazać wartości null jako nadawcę, gdy wywołaniem zdarzenia statyczne.</span><span class="sxs-lookup"><span data-stu-id="d5736-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="d5736-125">**X DO NOT** przekazać wartości null jako parametr danych zdarzenia, gdy wywołanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d5736-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="d5736-126">Należy przekazać `EventArgs.Empty`, jeśli nie chcesz przekazać żadnych danych do metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="d5736-127">Deweloperzy oczekują, że ten parametr nie ma wartości null.</span><span class="sxs-lookup"><span data-stu-id="d5736-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="d5736-128">**✓ CONSIDER** wywoływanie zdarzeń, które użytkownik końcowy może anulować.</span><span class="sxs-lookup"><span data-stu-id="d5736-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="d5736-129">Dotyczy to przede wszystkim zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="d5736-130">Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> lub jej podklasy jako argumentu zdarzenia, aby umożliwić użytkownikowi końcowemu anulowanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="d5736-131">Projekt programu obsługi zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d5736-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="d5736-132">Istnieją przypadki, w których nie można użyć `EventHandler<T>`, na przykład gdy struktura musi działać we wcześniejszych wersjach środowiska CLR, które nie obsługują typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="d5736-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="d5736-133">W takich przypadkach może być konieczne zaprojektowanie i opracowanie niestandardowego delegata obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="d5736-134">**✓ DO** zwracany typ void na użytek obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="d5736-135">Procedura obsługi zdarzeń może wywoływać wiele metod obsługi zdarzeń, prawdopodobnie na wielu obiektach.</span><span class="sxs-lookup"><span data-stu-id="d5736-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="d5736-136">Jeśli metody obsługi zdarzeń mogły zwrócić wartość, dla każdego wywołania zdarzenia może istnieć wiele wartości zwracanych.</span><span class="sxs-lookup"><span data-stu-id="d5736-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="d5736-137">**✓ DO** użyj `object` jako typ pierwszego parametru metody obsługi zdarzeń i nadaj mu `sender`.</span><span class="sxs-lookup"><span data-stu-id="d5736-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="d5736-138">**✓ DO** użyj <xref:System.EventArgs?displayProperty=nameWithType> ani jej podklasy jako typ drugiego parametru obsługi zdarzeń i nadaj mu `e`.</span><span class="sxs-lookup"><span data-stu-id="d5736-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="d5736-139">**X DO NOT** ma więcej niż dwa parametry dotyczące programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d5736-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="d5736-140">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="d5736-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d5736-141">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="d5736-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5736-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5736-142">See also</span></span>

- [<span data-ttu-id="d5736-143">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="d5736-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="d5736-144">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="d5736-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
