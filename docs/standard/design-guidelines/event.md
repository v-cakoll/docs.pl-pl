---
title: Projekt zdarzeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a07392ba805b5f2a3913b01a15dd0e1668f0ccf7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="event-design"></a><span data-ttu-id="1ce9b-102">Projekt zdarzeń</span><span class="sxs-lookup"><span data-stu-id="1ce9b-102">Event Design</span></span>
<span data-ttu-id="1ce9b-103">Zdarzenia są najczęściej używane formę wywołania zwrotne (konstrukcji umożliwiających framework do wywołania do kodu użytkownika).</span><span class="sxs-lookup"><span data-stu-id="1ce9b-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="1ce9b-104">Inne mechanizmy wywołania zwrotnego zawierać elementów członkowskich delegatów, wirtualne elementy członkowskie i oparty na używanie dodatków. Dane z badań użyteczność wskazania, że większość deweloperów wygodniejsze za pomocą zdarzeń, nie są one za pomocą innych mechanizmów wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="1ce9b-105">Zdarzenia są dobrze zintegrowane z usługą Visual Studio i wielu języków.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-105">Events are nicely integrated with Visual Studio and many languages.</span></span>  
  
 <span data-ttu-id="1ce9b-106">Należy pamiętać, że istnieją dwie grupy zdarzeń: zdarzenia wywoływane przed wykonaniem stan zmian w systemie, nazywanych zdarzeń poprzedzających i zdarzenia wywoływane po zmianie stanu, wywoływana po zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="1ce9b-107">Przykładem zdarzenia wstępnej może być `Form.Closing`, które jest wywoływane przed zamknięciem formularza.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="1ce9b-108">Przykładem zdarzenia po może być `Form.Closed`, które jest wywoływane po zamknięciu formularza.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>  
  
 <span data-ttu-id="1ce9b-109">**CZY ✓** używany jest termin "raise" dla zdarzenia, a nie "fire" lub "wyzwolenia".</span><span class="sxs-lookup"><span data-stu-id="1ce9b-109">**✓ DO** use the term "raise" for events rather than "fire" or "trigger."</span></span>  
  
 <span data-ttu-id="1ce9b-110">**CZY ✓** użyj <xref:System.EventHandler%601?displayProperty=nameWithType> zamiast ręcznego tworzenia nowych delegatów, które mają być używane jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-110">**✓ DO** use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>  
  
 <span data-ttu-id="1ce9b-111">**ROZWAŻ ✓** przy użyciu podklasą <xref:System.EventArgs> jako argument zdarzenia, jeśli nie masz pewności absolutnie zdarzenie nie będzie trzeba do przenoszenia danych do obsługi metody zdarzeń w takim przypadku można zastosować `EventArgs` wpisać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-111">**✓ CONSIDER** using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>  
  
 <span data-ttu-id="1ce9b-112">Jeśli dostarczany za pomocą interfejsu API `EventArgs` bezpośrednio, nigdy nie będą mogli dodawać żadnych danych do ze zdarzeniem bez przerywania zgodności.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="1ce9b-113">Jeśli używasz podklasy, nawet jeśli pierwotnie pusty, można dodać właściwości do podklasy w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>  
  
 <span data-ttu-id="1ce9b-114">**CZY ✓** Użyj chronione metody wirtualnej, aby wywołać każdego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-114">**✓ DO** use a protected virtual method to raise each event.</span></span> <span data-ttu-id="1ce9b-115">To ma zastosowanie tylko do niestatycznego zdarzeń w klasach niezapieczętowany, aby nie struktury, zapieczętowane klasy lub zdarzenia statyczne.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>  
  
 <span data-ttu-id="1ce9b-116">Celem metody jest sposób dla klasy pochodnej w celu obsługi zdarzeń za pomocą zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="1ce9b-117">Zastępowanie jest bardziej elastyczne, szybszy i bardziej naturalny sposób obsługi zdarzeń klasy podstawowej w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="1ce9b-118">Konwencja Nazwa metody powinna zaczynać się znakiem "On" i występować o nazwie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>  
  
 <span data-ttu-id="1ce9b-119">Klasa pochodna można zrezygnować z wywoływać implementację podstawową metody w jego zastąpienie.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="1ce9b-120">Należy przygotować to w tym wszystkie metody, która jest wymagana dla klasy podstawowej działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>  
  
 <span data-ttu-id="1ce9b-121">**CZY ✓** przyjmować jeden parametr do metody chronionych, która wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-121">**✓ DO** take one parameter to the protected method that raises an event.</span></span>  
  
 <span data-ttu-id="1ce9b-122">Parametr powinno być nazwanym `e` , należy wpisać jako klasa argumentów zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>  
  
 <span data-ttu-id="1ce9b-123">**X nie** należy przekazać wartość null jako nadawcę podczas wywołaniem Niestatyczne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-123">**X DO NOT** pass null as the sender when raising a nonstatic event.</span></span>  
  
 <span data-ttu-id="1ce9b-124">**CZY ✓** przekazać wartości null jako nadawcę, gdy wywołaniem zdarzenia statyczne.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-124">**✓ DO** pass null as the sender when raising a static event.</span></span>  
  
 <span data-ttu-id="1ce9b-125">**X nie** przekazać wartości null jako parametr danych zdarzenia, gdy wywołanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-125">**X DO NOT** pass null as the event data parameter when raising an event.</span></span>  
  
 <span data-ttu-id="1ce9b-126">Należy przekazać `EventArgs.Empty` Jeśli nie chcesz przekazać żadnych danych do obsługi metody zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="1ce9b-127">Deweloperzy oczekiwać, że ten parametr nie powinien być pusty.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-127">Developers expect this parameter not to be null.</span></span>  
  
 <span data-ttu-id="1ce9b-128">**ROZWAŻ ✓** wywoływanie zdarzeń, które użytkownik końcowy może anulować.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-128">**✓ CONSIDER** raising events that the end user can cancel.</span></span> <span data-ttu-id="1ce9b-129">Dotyczy to tylko zdarzeń poprzedzających.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-129">This only applies to pre-events.</span></span>  
  
 <span data-ttu-id="1ce9b-130">Użyj <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> ani jej podklasy jako argument zdarzenia, aby umożliwić użytkownikom końcowym Anulowanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>  
  
### <a name="custom-event-handler-design"></a><span data-ttu-id="1ce9b-131">Projekt programu obsługi zdarzeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="1ce9b-131">Custom Event Handler Design</span></span>  
 <span data-ttu-id="1ce9b-132">Istnieją przypadki, w którym `EventHandler<T>` nie można użyć, np. gdy platformę potrzebuje do pracy z wcześniejszych wersji środowiska CLR, która nie obsługuje typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="1ce9b-133">W takich przypadkach może być konieczne do projektowania i opracowywania delegata obsługi zdarzeń niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>  
  
 <span data-ttu-id="1ce9b-134">**CZY ✓** zwracany typ void na użytek obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-134">**✓ DO** use a return type of void for event handlers.</span></span>  
  
 <span data-ttu-id="1ce9b-135">Program obsługi zdarzeń może wywołać obsługi metod, prawdopodobnie na wiele obiektów wiele zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="1ce9b-136">Jeśli metody obsługi zdarzeń zostały może zwracać wartości, może to być wiele wartości zwrotnych dla każdego wywołania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>  
  
 <span data-ttu-id="1ce9b-137">**CZY ✓** użyj `object` jako typ pierwszego parametru metody obsługi zdarzeń i nadaj mu `sender`.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-137">**✓ DO** use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>  
  
 <span data-ttu-id="1ce9b-138">**CZY ✓** użyj <xref:System.EventArgs?displayProperty=nameWithType> ani jej podklasy jako typ drugiego parametru obsługi zdarzeń i nadaj mu `e`.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-138">**✓ DO** use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>  
  
 <span data-ttu-id="1ce9b-139">**X nie** ma więcej niż dwa parametry dotyczące programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1ce9b-139">**X DO NOT** have more than two parameters on event handlers.</span></span>  
  
 <span data-ttu-id="1ce9b-140">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="1ce9b-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1ce9b-141">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="1ce9b-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce9b-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ce9b-142">See Also</span></span>  
 [<span data-ttu-id="1ce9b-143">Element członkowski — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1ce9b-143">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="1ce9b-144">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="1ce9b-144">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
