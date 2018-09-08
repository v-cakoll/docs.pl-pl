---
title: Nazwy elementów członkowskich typu
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0541f100f208543c796de7238e68ea6f90c7b299
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44205182"
---
# <a name="names-of-type-members"></a><span data-ttu-id="49916-102">Nazwy elementów członkowskich typu</span><span class="sxs-lookup"><span data-stu-id="49916-102">Names of Type Members</span></span>
<span data-ttu-id="49916-103">Typy składają się z elementów członkowskich: metody, właściwości, zdarzenia, konstruktory i pola.</span><span class="sxs-lookup"><span data-stu-id="49916-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="49916-104">W poniższych sekcjach opisano zasady nazewnictwa elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="49916-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="49916-105">Nazwy metody</span><span class="sxs-lookup"><span data-stu-id="49916-105">Names of Methods</span></span>  
 <span data-ttu-id="49916-106">Ponieważ metody oznacza, że podjęcia działań, wytyczne dotyczące projektowania wymagają nazwy metod zleceń i fraz zlecenie.</span><span class="sxs-lookup"><span data-stu-id="49916-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="49916-107">Następujące ta wytyczna również służy do odróżnienia nazwy metod nazwy właściwości i typów, które są rzeczownik lub przymiotnik fraz.</span><span class="sxs-lookup"><span data-stu-id="49916-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="49916-108">**✓ DO** Nadaj nazwy metody, które mogą lub fraz zlecenie.</span><span class="sxs-lookup"><span data-stu-id="49916-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="49916-109">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="49916-109">Names of Properties</span></span>  
 <span data-ttu-id="49916-110">W przeciwieństwie do innych członków właściwości powinien być podawany przymiotników nazw lub frazy rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="49916-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="49916-111">To, ponieważ właściwość odnosi się do danych i nazwę właściwości odzwierciedlała to.</span><span class="sxs-lookup"><span data-stu-id="49916-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="49916-112">PascalCasing jest zawsze używany dla nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="49916-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="49916-113">**✓ DO** nazwę właściwości, za pomocą rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="49916-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="49916-114">**X DO NOT** mają właściwości, które zgodna z nazwą metody "Get", jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="49916-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="49916-115">Ten wzorzec zazwyczaj wskazuje, czy właściwość naprawdę powinna być metody.</span><span class="sxs-lookup"><span data-stu-id="49916-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="49916-116">**✓ DO** nazwy właściwości kolekcji o liczbie mnogiej frazę opisujące elementy w kolekcji, zamiast korzystać z pojedynczej frazy, a następnie "List" lub "Collection".</span><span class="sxs-lookup"><span data-stu-id="49916-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="49916-117">**✓ DO** nazwy właściwości logiczne z frazą wyraził (`CanSeek` zamiast `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="49916-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="49916-118">Opcjonalnie można także prefiks właściwości logiczne "Is", "możliwości" lub "Ma," tylko wtedy, gdy dodatkowe korzyści.</span><span class="sxs-lookup"><span data-stu-id="49916-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="49916-119">**✓ CONSIDER** zapewnia taką samą nazwę jak jego typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="49916-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="49916-120">Na przykład, następująca właściwość poprawnie pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc nosi nazwę właściwości `Color`:</span><span class="sxs-lookup"><span data-stu-id="49916-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="49916-121">Nazwy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="49916-121">Names of Events</span></span>  
 <span data-ttu-id="49916-122">Zdarzenia zawsze odwołuje się do niektórych akcji, który jest występuje albo, który wystąpił.</span><span class="sxs-lookup"><span data-stu-id="49916-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="49916-123">W związku z tym podobnie jak w przypadku metod, zdarzeń są nazywane zleceń i czasu teraźniejszego zlecenia służy do wskazywania czasu, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="49916-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="49916-124">**✓ DO** nazwy zdarzeń za pomocą zlecenie lub zlecenia frazę.</span><span class="sxs-lookup"><span data-stu-id="49916-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="49916-125">Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="49916-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="49916-126">**✓ DO** nadać nazwy zdarzenia przy użyciu koncepcji przed i po nim, za pomocą obecny i czasy w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="49916-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="49916-127">Na przykład, czy można wywołać Zamknij zdarzenie, które jest wywoływane przed zamknięciem okna `Closing`, i może być wywoływana taki, który jest uruchamiany po zamknięciu okna `Closed`.</span><span class="sxs-lookup"><span data-stu-id="49916-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="49916-128">**X DO NOT** Użyj "Before" lub "After" prefiksy lub postfixes, aby wskazać, przed i po zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="49916-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="49916-129">Użyj obecne i czasy ostatnich, jak opisano powyżej.</span><span class="sxs-lookup"><span data-stu-id="49916-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="49916-130">**✓ DO** nazwy programów obsługi zdarzeń (używany jako typy zdarzeń delegaty) wraz z sufiksem "EventHandler", jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="49916-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="49916-131">**✓ DO** korzystanie z dwóch parametrów o nazwie `sender` i `e` w procedurze obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="49916-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="49916-132">Parametr sender reprezentuje obiekt, który spowodował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="49916-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="49916-133">Parametr sender jest zazwyczaj typu `object`nawet wtedy, gdy można stosować bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="49916-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="49916-134">**✓ DO** nazwy zdarzeń klasy argumentu z sufiksem "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="49916-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="49916-135">Nazwy pól</span><span class="sxs-lookup"><span data-stu-id="49916-135">Names of Fields</span></span>  
 <span data-ttu-id="49916-136">Wskazówki dotyczące nazewnictwa pól dotyczą pola statyczne publiczne i chronione.</span><span class="sxs-lookup"><span data-stu-id="49916-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="49916-137">Wewnętrzne i prywatne pola nie są objęte wytyczne i pola publiczne lub chronione wystąpienie nie są dozwolone w [element członkowski — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="49916-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="49916-138">**✓ DO** Użyj PascalCasing w nazwach pól.</span><span class="sxs-lookup"><span data-stu-id="49916-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="49916-139">**✓ DO** nazwać pola, przy użyciu rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="49916-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="49916-140">**X DO NOT** używać prefiksu dla nazw pól.</span><span class="sxs-lookup"><span data-stu-id="49916-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="49916-141">Na przykład nie umożliwia "g_" lub "s_" oznaczają pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="49916-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="49916-142">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="49916-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="49916-143">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="49916-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49916-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49916-144">See also</span></span>

- [<span data-ttu-id="49916-145">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="49916-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="49916-146">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="49916-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
