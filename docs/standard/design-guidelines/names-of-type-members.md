---
title: "Nazwy elementów członkowskich typu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d489d4cf61adfe8550bd16b85cd658e0d545c861
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-type-members"></a><span data-ttu-id="63d48-102">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="63d48-102">Names of Type Members</span></span>
<span data-ttu-id="63d48-103">Typy składają się z elementów członkowskich: metody, właściwości, zdarzenia, konstruktorów i pól.</span><span class="sxs-lookup"><span data-stu-id="63d48-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="63d48-104">W poniższych sekcjach opisano zasady nazewnictwa elementy członkowskie typu.</span><span class="sxs-lookup"><span data-stu-id="63d48-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="63d48-105">Nazwy metod</span><span class="sxs-lookup"><span data-stu-id="63d48-105">Names of Methods</span></span>  
 <span data-ttu-id="63d48-106">Ponieważ metody służą do podjęcia działań, zaleceń dotyczących projektowania wymagają nazwy metod zleceń ani fraz zlecenia.</span><span class="sxs-lookup"><span data-stu-id="63d48-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="63d48-107">Również po ta wytyczna służy do odróżnienia nazwy metod nazw właściwości i typów, które są rzeczownik lub przymiotnik fraz.</span><span class="sxs-lookup"><span data-stu-id="63d48-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="63d48-108">**CZY ✓** Nadaj nazwy metody, które mogą lub zlecenie fraz.</span><span class="sxs-lookup"><span data-stu-id="63d48-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="63d48-109">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="63d48-109">Names of Properties</span></span>  
 <span data-ttu-id="63d48-110">W przeciwieństwie do innych członków właściwości powinny mieć nazwy przymiotników lub frazę rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="63d48-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="63d48-111">Wynika to z właściwością odnosi się do danych i odzwierciedla nazwę właściwości, która.</span><span class="sxs-lookup"><span data-stu-id="63d48-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="63d48-112">PascalCasing zawsze jest używany dla nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="63d48-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="63d48-113">**CZY ✓** nazwy właściwości za pomocą rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="63d48-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="63d48-114">**X nie** właściwości pasujących do nazwy metody "Get", jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="63d48-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="63d48-115">Ten wzorzec zazwyczaj wskazuje, że właściwość naprawdę powinna być metody.</span><span class="sxs-lookup"><span data-stu-id="63d48-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="63d48-116">**CZY ✓** nazwy właściwości kolekcji o liczbie mnogiej frazy opisujące elementów w kolekcji zamiast za pomocą pojedynczej frazy "List" lub "Collection".</span><span class="sxs-lookup"><span data-stu-id="63d48-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="63d48-117">**CZY ✓** nazwę logiczną właściwości frazą potwierdzającego (`CanSeek` zamiast `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="63d48-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="63d48-118">Opcjonalnie można również prefiksu logiczną właściwości z "Is", "można" lub "Ma," tylko wtedy, gdy dodaje wartość.</span><span class="sxs-lookup"><span data-stu-id="63d48-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="63d48-119">**ROZWAŻ ✓** nadanie właściwości taką samą nazwę jak jego typu.</span><span class="sxs-lookup"><span data-stu-id="63d48-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="63d48-120">Na przykład następująca właściwość poprawnie pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc nosi nazwę właściwości `Color`:</span><span class="sxs-lookup"><span data-stu-id="63d48-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="63d48-121">Nazwy zdarzenia</span><span class="sxs-lookup"><span data-stu-id="63d48-121">Names of Events</span></span>  
 <span data-ttu-id="63d48-122">Zdarzenia zawsze odwołuje się do niektórych działań, albo jest w toku lub, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="63d48-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="63d48-123">W związku z tym tak jak w przypadku metod, zdarzenia są nazywane zleceń, a czas zlecenie jest używany do określania czasu, gdy zdarzenie zostanie wywołane.</span><span class="sxs-lookup"><span data-stu-id="63d48-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="63d48-124">**CZY ✓** Nazwa zdarzenia z zlecenie lub zlecenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="63d48-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="63d48-125">Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="63d48-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="63d48-126">**CZY ✓** nadać nazwy zdarzenia z koncepcji przed i po, przy użyciu obecny i użycie czasów w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="63d48-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="63d48-127">Na przykład, czy można wywołać zamknięcia zdarzenie, które jest wywoływane przed zamknięciem okna `Closing`, i czy można wywołać, który jest uruchamiany po zamknięciu okna `Closed`.</span><span class="sxs-lookup"><span data-stu-id="63d48-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="63d48-128">**X nie** Użyj "Przed" lub "Po" prefiksy lub postfixes, aby wskazać przed i po zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="63d48-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="63d48-129">Użyj obecne i użycie czasów przeszłości zgodnie z opisem tylko.</span><span class="sxs-lookup"><span data-stu-id="63d48-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="63d48-130">**CZY ✓** Nazwa procedury obsługi zdarzeń (obiekty delegowane używane jako typy zdarzeń) wraz z sufiksem "EventHandler", jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="63d48-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="63d48-131">**CZY ✓** dwa parametry o nazwie `sender` i `e` w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="63d48-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="63d48-132">Parametr nadawcy reprezentuje obiekt, który wywołał zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="63d48-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="63d48-133">Parametr nadawcy jest zwykle typu `object`nawet wtedy, gdy można zastosować bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="63d48-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="63d48-134">**CZY ✓** Nazwa zdarzenia klasy argument wraz z sufiksem "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="63d48-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="63d48-135">Nazwy pól</span><span class="sxs-lookup"><span data-stu-id="63d48-135">Names of Fields</span></span>  
 <span data-ttu-id="63d48-136">Wskazówki dotyczące nazewnictwa pola dotyczą pola statyczne publiczne i chronione.</span><span class="sxs-lookup"><span data-stu-id="63d48-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="63d48-137">Pola wewnętrzne i prywatne nie są objęte wytycznych i pól wystąpień publiczne lub chronione nie są dozwolone w [zaleceń dotyczących projektowania elementu członkowskiego](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="63d48-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="63d48-138">**CZY ✓** Użyj PascalCasing w nazwach pól.</span><span class="sxs-lookup"><span data-stu-id="63d48-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="63d48-139">**CZY ✓** nazwy pól przy użyciu rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="63d48-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="63d48-140">**X nie** użyć prefiksu nazwy pól.</span><span class="sxs-lookup"><span data-stu-id="63d48-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="63d48-141">Na przykład nie umożliwia "g_" lub "s_" wskazują pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="63d48-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="63d48-142">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="63d48-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="63d48-143">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="63d48-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d48-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63d48-144">See Also</span></span>  
 [<span data-ttu-id="63d48-145">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="63d48-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="63d48-146">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="63d48-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
