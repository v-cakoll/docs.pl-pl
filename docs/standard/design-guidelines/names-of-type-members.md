---
title: Nazwy składowych typu
ms.date: 10/22/2008
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
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353708"
---
# <a name="names-of-type-members"></a><span data-ttu-id="ac89d-102">Nazwy składowych typu</span><span class="sxs-lookup"><span data-stu-id="ac89d-102">Names of Type Members</span></span>
<span data-ttu-id="ac89d-103">Typy składowe są elementami członkowskimi: metodami, właściwościami, zdarzeniami, konstruktorami i polami.</span><span class="sxs-lookup"><span data-stu-id="ac89d-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="ac89d-104">W poniższych sekcjach opisano wskazówki dotyczące nazewnictwa elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="ac89d-104">The following sections describe guidelines for naming type members.</span></span>  
  
## <a name="names-of-methods"></a><span data-ttu-id="ac89d-105">Nazwy metod</span><span class="sxs-lookup"><span data-stu-id="ac89d-105">Names of Methods</span></span>  
 <span data-ttu-id="ac89d-106">Ponieważ metody są metodą podjęcia działania, wskazówki dotyczące projektowania wymagają, aby nazwy metod były czasownikami lub wyrażeniami czasownikowymi.</span><span class="sxs-lookup"><span data-stu-id="ac89d-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="ac89d-107">Poniższe wytyczne umożliwiają również odróżnianie nazw metod od nazw właściwości i typów, które są frazami rzeczownikmi lub przymiotnikami.</span><span class="sxs-lookup"><span data-stu-id="ac89d-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>  
  
 <span data-ttu-id="ac89d-108">**✓ DO** Nadaj nazwy metody, które mogą lub fraz zlecenie.</span><span class="sxs-lookup"><span data-stu-id="ac89d-108">**✓ DO** give methods names that are verbs or verb phrases.</span></span>  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a><span data-ttu-id="ac89d-109">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="ac89d-109">Names of Properties</span></span>  
 <span data-ttu-id="ac89d-110">W przeciwieństwie do innych elementów członkowskich, właściwości powinny zawierać frazę rzeczowników lub nazwy przymiotników.</span><span class="sxs-lookup"><span data-stu-id="ac89d-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="ac89d-111">Oznacza to, że Właściwość odwołuje się do danych, a nazwa właściwości odzwierciedla to.</span><span class="sxs-lookup"><span data-stu-id="ac89d-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="ac89d-112">PascalCasing jest zawsze używana dla nazw właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac89d-112">PascalCasing is always used for property names.</span></span>  
  
 <span data-ttu-id="ac89d-113">**✓ DO** nazwę właściwości, za pomocą rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="ac89d-113">**✓ DO** name properties using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="ac89d-114">**X DO NOT** mają właściwości, które zgodna z nazwą metody "Get", jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac89d-114">**X DO NOT** have properties that match the name of "Get" methods as in the following example:</span></span>  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 <span data-ttu-id="ac89d-115">Ten wzorzec zazwyczaj wskazuje, że właściwość powinna być w rzeczywistości metodą.</span><span class="sxs-lookup"><span data-stu-id="ac89d-115">This pattern typically indicates that the property should really be a method.</span></span>  
  
 <span data-ttu-id="ac89d-116">**✓ DO** nazwy właściwości kolekcji o liczbie mnogiej frazę opisujące elementy w kolekcji, zamiast korzystać z pojedynczej frazy, a następnie "List" lub "Collection".</span><span class="sxs-lookup"><span data-stu-id="ac89d-116">**✓ DO** name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection."</span></span>  
  
 <span data-ttu-id="ac89d-117">**✓ DO** nazwy właściwości logiczne z frazą wyraził (`CanSeek` zamiast `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="ac89d-117">**✓ DO** name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="ac89d-118">Opcjonalnie można również prefiksować właściwości logiczne z "is", "" lub "ma", ale tylko wtedy, gdy dodaje wartość.</span><span class="sxs-lookup"><span data-stu-id="ac89d-118">Optionally, you can also prefix Boolean properties with "Is," "Can," or "Has," but only where it adds value.</span></span>  
  
 <span data-ttu-id="ac89d-119">**✓ CONSIDER** zapewnia taką samą nazwę jak jego typ właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac89d-119">**✓ CONSIDER** giving a property the same name as its type.</span></span>  
  
 <span data-ttu-id="ac89d-120">Na przykład następująca Właściwość prawidłowo pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc właściwość ma nazwę `Color`:</span><span class="sxs-lookup"><span data-stu-id="ac89d-120">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a><span data-ttu-id="ac89d-121">Nazwy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="ac89d-121">Names of Events</span></span>  
 <span data-ttu-id="ac89d-122">Zdarzenia zawsze odwołują się do niektórych akcji, takich, które są wykonywane lub takie, które wystąpiły.</span><span class="sxs-lookup"><span data-stu-id="ac89d-122">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="ac89d-123">W związku z tym, podobnie jak w przypadku metod, zdarzenia są nazwane przy użyciu czasowników, a w celu wskazania czasu, gdy zdarzenie jest zgłaszane, używana jest wartość zlecenia.</span><span class="sxs-lookup"><span data-stu-id="ac89d-123">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>  
  
 <span data-ttu-id="ac89d-124">**✓ DO** nazwy zdarzeń za pomocą zlecenie lub zlecenia frazę.</span><span class="sxs-lookup"><span data-stu-id="ac89d-124">**✓ DO** name events with a verb or a verb phrase.</span></span>  
  
 <span data-ttu-id="ac89d-125">Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="ac89d-125">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>  
  
 <span data-ttu-id="ac89d-126">**✓ DO** nadać nazwy zdarzenia przy użyciu koncepcji przed i po nim, za pomocą obecny i czasy w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="ac89d-126">**✓ DO** give events names with a concept of before and after, using the present and past tenses.</span></span>  
  
 <span data-ttu-id="ac89d-127">Na przykład zdarzenie zamykające wywoływane przed zamknięciem okna powinno być wywoływane `Closing`, a jeden, który jest wywoływany po zamknięciu okna, zostanie wywołany `Closed`.</span><span class="sxs-lookup"><span data-stu-id="ac89d-127">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>  
  
 <span data-ttu-id="ac89d-128">**X DO NOT** Użyj "Before" lub "After" prefiksy lub postfixes, aby wskazać, przed i po zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ac89d-128">**X DO NOT** use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="ac89d-129">Użyj obecnych i ostatnich dziesiątek tak samo, jak zostało to opisane.</span><span class="sxs-lookup"><span data-stu-id="ac89d-129">Use present and past tenses as just described.</span></span>  
  
 <span data-ttu-id="ac89d-130">**✓ DO** nazwy programów obsługi zdarzeń (używany jako typy zdarzeń delegaty) wraz z sufiksem "EventHandler", jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ac89d-130">**✓ DO** name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 <span data-ttu-id="ac89d-131">**✓ DO** korzystanie z dwóch parametrów o nazwie `sender` i `e` w procedurze obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ac89d-131">**✓ DO** use two parameters named `sender` and `e` in event handlers.</span></span>  
  
 <span data-ttu-id="ac89d-132">Parametr Sender reprezentuje obiekt, który spowodował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="ac89d-132">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="ac89d-133">Parametr nadawcy jest zazwyczaj typu `object`, nawet jeśli można użyć bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="ac89d-133">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>  
  
 <span data-ttu-id="ac89d-134">**✓ DO** nazwy zdarzeń klasy argumentu z sufiksem "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="ac89d-134">**✓ DO** name event argument classes with the "EventArgs" suffix.</span></span>  
  
## <a name="names-of-fields"></a><span data-ttu-id="ac89d-135">Nazwy pól</span><span class="sxs-lookup"><span data-stu-id="ac89d-135">Names of Fields</span></span>  
 <span data-ttu-id="ac89d-136">Wskazówki dotyczące nazewnictwa pól mają zastosowanie do statycznych pól publicznych i chronionych.</span><span class="sxs-lookup"><span data-stu-id="ac89d-136">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="ac89d-137">Pola wewnętrzne i prywatne nie są objęte wskazówkami, a pola Public lub Protected instance są niedozwolone w [wytycznych dotyczących projektowania elementu członkowskiego](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="ac89d-137">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>  
  
 <span data-ttu-id="ac89d-138">**✓ DO** Użyj PascalCasing w nazwach pól.</span><span class="sxs-lookup"><span data-stu-id="ac89d-138">**✓ DO** use PascalCasing in field names.</span></span>  
  
 <span data-ttu-id="ac89d-139">**✓ DO** nazwać pola, przy użyciu rzeczownik, rzeczownik frazy lub przymiotnik.</span><span class="sxs-lookup"><span data-stu-id="ac89d-139">**✓ DO** name fields using a noun, noun phrase, or adjective.</span></span>  
  
 <span data-ttu-id="ac89d-140">**X DO NOT** używać prefiksu dla nazw pól.</span><span class="sxs-lookup"><span data-stu-id="ac89d-140">**X DO NOT** use a prefix for field names.</span></span>  
  
 <span data-ttu-id="ac89d-141">Na przykład nie umożliwia "g_" lub "s_" oznaczają pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="ac89d-141">For example, do not use "g_" or "s_" to indicate static fields.</span></span>  
  
 <span data-ttu-id="ac89d-142">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="ac89d-142">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="ac89d-143">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="ac89d-143">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac89d-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac89d-144">See also</span></span>

- [<span data-ttu-id="ac89d-145">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="ac89d-145">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="ac89d-146">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="ac89d-146">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
