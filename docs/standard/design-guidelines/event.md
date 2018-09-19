---
title: Projekt zdarzenia
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b257da73d33fae54ef464e9dd69906316b87fd88
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46288280"
---
# <a name="event-design"></a><span data-ttu-id="4809c-102">Projekt zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4809c-102">Event Design</span></span>
<span data-ttu-id="4809c-103">Zdarzenia są najczęściej używane formularza wywołania zwrotne (konstrukcji, zezwalających na platformę, by mogą wywoływać kodu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="4809c-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="4809c-104">Inne mechanizmy wywołania zwrotnego dołączone elementy członkowskie, biorąc delegatów, wirtualne elementy członkowskie i oparte na interfejsie wtyczki. Dane z badań użyteczność wskazać, że większość deweloperów bardziej komfortowo, jednocześnie za pomocą zdarzeń, niż użytkownicy korzystają z innych mechanizmów wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4809c-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="4809c-105">Zdarzenia są dobrze zintegrowane z Visual Studio i wielu języków.</span><span class="sxs-lookup"><span data-stu-id="4809c-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="4809c-106">Ważne jest, aby zwrócić uwagę na dwie grupy zdarzeń: zdarzenia wywoływane przed wykonaniem stan zmiany systemu, nazywany zdarzeń poprzedzających i zdarzenia wywoływane po zmianie stanu, wywoływana po zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="4809c-107">Oto przykład zdarzenia poprzedzającego `Form.Closing`, które jest wywoływane przed zamknięciem formularza.</span><span class="sxs-lookup"><span data-stu-id="4809c-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="4809c-108">Oto przykład zdarzenia po `Form.Closed`, które jest wywoływane po zamknięciu formularza.</span><span class="sxs-lookup"><span data-stu-id="4809c-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="4809c-109">**✓ DO** używany jest termin "raise" dla zdarzenia, a nie "fire" lub "wyzwolenia".</span><span class="sxs-lookup"><span data-stu-id="4809c-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="4809c-110">**✓ DO** użyj <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4809c-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="4809c-111">**✓ CONSIDER** przy użyciu podklasą <xref:System.EventArgs> jako argument zdarzenia, jeśli nie masz pewności absolutnie zdarzenie nie będzie trzeba do przenoszenia danych do obsługi metody zdarzeń w takim przypadku można zastosować `EventArgs` wpisać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="4809c-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="4809c-112">Jeśli dostarczasz interfejsu API przy użyciu `EventArgs` bezpośrednio, nigdy nie będą mogli dodawać żadnych danych, które mają znajdować się ze zdarzeniem bez przerywania zgodność.</span><span class="sxs-lookup"><span data-stu-id="4809c-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="4809c-113">Jeśli używasz podklasę, nawet jeśli początkowo całkowicie pusty, można dodać właściwości do podklasy w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="4809c-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="4809c-114">**✓ DO** Użyj chronione metody wirtualnej, aby wywołać każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="4809c-115">To ma zastosowanie tylko do niestatycznego zdarzenia niezapieczętowane klasy, aby nie struktury, zapieczętowane klasy lub zdarzenia statyczne.</span><span class="sxs-lookup"><span data-stu-id="4809c-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="4809c-116">Przeznaczenie metody jest sposób dla klasy pochodnej do obsługi zdarzeń za pomocą zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="4809c-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="4809c-117">Zastępowanie jest bardziej elastyczna, szybsze i bardziej naturalny sposób obsługi zdarzeń klasy podstawowej w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="4809c-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="4809c-118">Zgodnie z Konwencją Nazwa metody powinna rozpoczynać się "On" i występować z nazwą zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="4809c-119">Klasa pochodna może zrezygnować z wywoływać implementację podstawową metody w jego zastąpienie.</span><span class="sxs-lookup"><span data-stu-id="4809c-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="4809c-120">Należy przygotować to przez nieumieszczenie jakiegokolwiek przetwarzania w metodzie, która jest wymagana dla klasy bazowej działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="4809c-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="4809c-121">**✓ DO** przyjmować jeden parametr do metody chronionych, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4809c-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="4809c-122">Powinien zostać nazwany parametr `e` , należy wpisać jako klasa argumentów zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="4809c-123">**X DO NOT** należy przekazać wartość null jako nadawcę podczas wywołaniem Niestatyczne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="4809c-124">**✓ DO** przekazać wartości null jako nadawcę, gdy wywołaniem zdarzenia statyczne.</span><span class="sxs-lookup"><span data-stu-id="4809c-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="4809c-125">**X DO NOT** przekazać wartości null jako parametr danych zdarzenia, gdy wywołanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="4809c-126">Należy przekazać `EventArgs.Empty` Jeśli nie chcesz przekazywać żadnych danych do metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4809c-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="4809c-127">Deweloperzy oczekiwać, że ten parametr nie mają one wartość null.</span><span class="sxs-lookup"><span data-stu-id="4809c-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="4809c-128">**✓ CONSIDER** wywoływanie zdarzeń, które użytkownik końcowy może anulować.</span><span class="sxs-lookup"><span data-stu-id="4809c-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="4809c-129">Dotyczy to tylko zdarzeń poprzedzających.</span><span class="sxs-lookup"><span data-stu-id="4809c-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="4809c-130">Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> lub jego podklasy jako argumentu zdarzenia, aby zezwolić użytkownikom na anulowanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="4809c-131">Projekt programu obsługi zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="4809c-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="4809c-132">Istnieją przypadki, w którym `EventHandler<T>` nie można użyć, np. gdy struktura potrzebuje do pracy z wcześniejszych wersji środowiska CLR, która nie obsługuje typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="4809c-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="4809c-133">W takich przypadkach może być konieczne projektowania i tworzenia delegata obsługi zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="4809c-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="4809c-134">**✓ DO** zwracany typ void na użytek obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4809c-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="4809c-135">Program obsługi zdarzeń można wywołać wiele obsługi metod, prawdopodobnie na wielu obiektach zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4809c-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="4809c-136">Jeśli zezwolono na metody obsługi zdarzeń w celu zwrócenia wartości, może to być wiele wartości zwracane dla każdego wywołania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4809c-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="4809c-137">**✓ DO** użyj `object` jako typ pierwszego parametru metody obsługi zdarzeń i nadaj mu `sender`.</span><span class="sxs-lookup"><span data-stu-id="4809c-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="4809c-138">**✓ DO** użyj <xref:System.EventArgs?displayProperty=nameWithType> ani jej podklasy jako typ drugiego parametru obsługi zdarzeń i nadaj mu `e`.</span><span class="sxs-lookup"><span data-stu-id="4809c-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="4809c-139">**X DO NOT** ma więcej niż dwa parametry dotyczące programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4809c-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="4809c-140">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="4809c-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4809c-141">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="4809c-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4809c-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4809c-142">See also</span></span>

- [<span data-ttu-id="4809c-143">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="4809c-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="4809c-144">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="4809c-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
