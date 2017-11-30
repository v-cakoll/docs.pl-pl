---
title: "Właściwości projektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 477b3b69ce1b8a3bb160e8e120885239e3d99e56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-design"></a><span data-ttu-id="46bdc-102">Właściwości projektu</span><span class="sxs-lookup"><span data-stu-id="46bdc-102">Property Design</span></span>
<span data-ttu-id="46bdc-103">Właściwości są technicznie bardzo podobna do metody, są one zupełnie różne pod względem ich scenariusze użycia.</span><span class="sxs-lookup"><span data-stu-id="46bdc-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="46bdc-104">Powinny one widoczne jako inteligentny pola.</span><span class="sxs-lookup"><span data-stu-id="46bdc-104">They should be seen as smart fields.</span></span> <span data-ttu-id="46bdc-105">Mają one składnia wywoływania pól i elastyczności metody.</span><span class="sxs-lookup"><span data-stu-id="46bdc-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="46bdc-106">**CZY ✓** utworzenie właściwości tylko do pobrania, jeśli element wywołujący nie ma być można zmienić wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="46bdc-107">Należy pamiętać, że jeśli typ właściwości jest typem referencyjnym modyfikowalna, wartość właściwości jest możliwa, nawet jeśli właściwość jest tylko do pobrania.</span><span class="sxs-lookup"><span data-stu-id="46bdc-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="46bdc-108">**X nie** Podaj setter o dostępności szerszym niż metoda pobierająca właściwości tylko do zestawu lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="46bdc-109">Na przykład nie należy używać właściwości z publicznej metody ustawiającej i chronione metody pobierającej.</span><span class="sxs-lookup"><span data-stu-id="46bdc-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="46bdc-110">Jeśli metoda pobierająca właściwości nie można podać, należy zaimplementować tę funkcję, co metoda.</span><span class="sxs-lookup"><span data-stu-id="46bdc-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="46bdc-111">Należy rozważyć uruchomienie nazwę metody z `Set` i postępuj zgodnie z co może mieć nosi nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="46bdc-112">Na przykład <xref:System.AppDomain> ma metodę o nazwie `SetCachePath` zamiast właściwość tylko do zestawu o nazwie `CachePath`.</span><span class="sxs-lookup"><span data-stu-id="46bdc-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="46bdc-113">**CZY ✓** podać za pośrednictwem domyślne wartości dla wszystkich właściwości, zapewniając, że wartości domyślne nie powodują luka w zabezpieczeniach lub poważny niewydajny kod.</span><span class="sxs-lookup"><span data-stu-id="46bdc-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="46bdc-114">**CZY ✓** umożliwia właściwości można ustawić w dowolnej kolejności, nawet jeśli spowoduje to tymczasowe nieprawidłowy stan obiektu.</span><span class="sxs-lookup"><span data-stu-id="46bdc-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="46bdc-115">Bardzo często dwóch lub więcej właściwości do punktu, w której niektóre wartości jedną właściwość może być nieprawidłowy powiązanych podane wartości innych właściwości w tym samym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="46bdc-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="46bdc-116">W takich przypadkach należy odroczyć wyjątki wynikające z nieprawidłowym stanie dopóki wzajemnie powiązanych właściwości są rzeczywiście używane razem z obiektu.</span><span class="sxs-lookup"><span data-stu-id="46bdc-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="46bdc-117">**CZY ✓** zachować poprzedniej wartości, jeśli metody ustawiającej właściwość zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="46bdc-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="46bdc-118">**X należy UNIKAĆ** zgłaszanie wyjątków z pobierających właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="46bdc-119">Metody pobierające właściwości powinny być proste operacje i nie powinny mieć wszystkie warunki wstępne.</span><span class="sxs-lookup"><span data-stu-id="46bdc-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="46bdc-120">Jeśli metoda pobierająca może zgłosić wyjątek, prawdopodobnie powinien przeprojektowany jako metodę.</span><span class="sxs-lookup"><span data-stu-id="46bdc-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="46bdc-121">Należy zauważyć, że ta zasada nie ma zastosowania do indeksatorów, gdzie oczekiwane wyjątki w wyniku sprawdzania poprawności argumentów.</span><span class="sxs-lookup"><span data-stu-id="46bdc-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="46bdc-122">Właściwość indeksowana projektu</span><span class="sxs-lookup"><span data-stu-id="46bdc-122">Indexed Property Design</span></span>  
 <span data-ttu-id="46bdc-123">Właściwość indeksowana jest specjalne właściwości, która może mieć parametrów i może być wywołany z specjalne składnię indeksowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="46bdc-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="46bdc-124">Właściwości indeksowane są często nazywane indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="46bdc-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="46bdc-125">Indeksatory powinna być używana tylko w interfejsów API, które zapewniają dostęp do elementów w kolekcji logiczne.</span><span class="sxs-lookup"><span data-stu-id="46bdc-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="46bdc-126">Na przykład ciąg to zbiór znaków i indeksatora na <xref:System.String?displayProperty=nameWithType> został dodany do dostęp do jego znaków.</span><span class="sxs-lookup"><span data-stu-id="46bdc-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="46bdc-127">**ROZWAŻ ✓** przy użyciu indeksatorów w celu zapewnienia dostępu do danych przechowywanych w tablicy wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="46bdc-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="46bdc-128">**ROZWAŻ ✓** udostępnia indeksatory na typy reprezentujące kolekcje elementów.</span><span class="sxs-lookup"><span data-stu-id="46bdc-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="46bdc-129">**X należy UNIKAĆ** przy użyciu indeksowane właściwości z więcej niż jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="46bdc-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="46bdc-130">Jeśli projekt wymaga kilku parametrów, rozważenia, czy właściwość naprawdę reprezentuje metody dostępu do kolekcji logiczne.</span><span class="sxs-lookup"><span data-stu-id="46bdc-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="46bdc-131">Jeśli nie, należy użyć metody.</span><span class="sxs-lookup"><span data-stu-id="46bdc-131">If it does not, use methods instead.</span></span> <span data-ttu-id="46bdc-132">Należy rozważyć uruchomienie nazwę metody z `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="46bdc-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="46bdc-133">**X należy UNIKAĆ** indeksatory z typami parametrów innych niż <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, lub wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="46bdc-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="46bdc-134">Jeśli projekt wymaga innych typów parametrów, a silnie obliczyć ponownie czy naprawdę interfejsu API reprezentuje metody dostępu do kolekcji logiczne.</span><span class="sxs-lookup"><span data-stu-id="46bdc-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="46bdc-135">Jeśli nie, należy użyć metody.</span><span class="sxs-lookup"><span data-stu-id="46bdc-135">If it does not, use a method.</span></span> <span data-ttu-id="46bdc-136">Należy rozważyć uruchomienie nazwę metody z `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="46bdc-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="46bdc-137">**CZY ✓** Użyj nazwy `Item` dla właściwości indeksowanych, chyba że istnieje lepsze oczywiście nazwa (np. zobacz <xref:System.String.Chars%2A> właściwość `System.String`).</span><span class="sxs-lookup"><span data-stu-id="46bdc-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="46bdc-138">W języku C# indeksatory są domyślnie nazwanego elementu.</span><span class="sxs-lookup"><span data-stu-id="46bdc-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="46bdc-139"><xref:System.Runtime.CompilerServices.IndexerNameAttribute> Można dostosować tę nazwę.</span><span class="sxs-lookup"><span data-stu-id="46bdc-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="46bdc-140">**X nie** zapewniają zarówno indeksatora, jak i metody, które są semantycznie równoważne.</span><span class="sxs-lookup"><span data-stu-id="46bdc-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="46bdc-141">**X nie** zapewniają więcej niż jednej rodziny przeciążone indeksatorów w jednym typie.</span><span class="sxs-lookup"><span data-stu-id="46bdc-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="46bdc-142">Ta wartość jest wymuszana przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="46bdc-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="46bdc-143">**X nie** niestandardowy użycie właściwości indeksowanych.</span><span class="sxs-lookup"><span data-stu-id="46bdc-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="46bdc-144">Ta wartość jest wymuszana przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="46bdc-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="46bdc-145">Zdarzenia powiadomień zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="46bdc-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="46bdc-146">Czasami jest wprowadzenie zdarzenie powiadomienia użytkownika o zmianach w wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="46bdc-147">Na przykład `System.Windows.Forms.Control` zgłasza `TextChanged` zdarzeń po wartości jego `Text` właściwość zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="46bdc-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="46bdc-148">**ROZWAŻ ✓** wywoływanie zmienić zdarzenia powiadomień po zmodyfikowaniu wartości właściwości ogólnych interfejsów API (zazwyczaj projektanta składników).</span><span class="sxs-lookup"><span data-stu-id="46bdc-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="46bdc-149">W przypadku scenariusza dobrej dla użytkownika dowiedzieć się, gdy Trwa zmienianie właściwości obiektu, obiekt powinien podnieść zdarzenia powiadomień zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="46bdc-150">Jednak jest mało prawdopodobne, aby warto obciążenie wywołania takich zdarzeń dla interfejsów API niskiego poziomu, takich jak typy podstawowe lub kolekcji.</span><span class="sxs-lookup"><span data-stu-id="46bdc-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="46bdc-151">Na przykład <xref:System.Collections.Generic.List%601> nie wywołałoby takie zdarzenia po dodaniu nowego elementu do listy i `Count` zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="46bdc-152">**ROZWAŻ ✓** wywoływanie zmienić zdarzenia powiadomień za pomocą zewnętrznego wymusza po zmianie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="46bdc-153">W przypadku zmiany wartości właściwości za pośrednictwem niektórych siły zewnętrzne (w sposób inny niż przez wywołanie metody obiektu), zgłoś zdarzenia wskazują deweloperowi, że wartość zmienia się i został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="46bdc-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="46bdc-154">Dobrym przykładem jest `Text` właściwości formantu pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="46bdc-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="46bdc-155">Gdy użytkownik wpisze tekst w `TextBox`, automatycznie zmienia się wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="46bdc-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="46bdc-156">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="46bdc-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="46bdc-157">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="46bdc-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46bdc-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46bdc-158">See Also</span></span>  
 [<span data-ttu-id="46bdc-159">Wytyczne dotyczące projektowania elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="46bdc-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="46bdc-160">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="46bdc-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
