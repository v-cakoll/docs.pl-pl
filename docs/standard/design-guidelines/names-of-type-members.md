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
ms.openlocfilehash: 81c837bd045992043208a59f6ee16803c1d6eb3c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744180"
---
# <a name="names-of-type-members"></a><span data-ttu-id="163c3-102">Nazwy składowych typu</span><span class="sxs-lookup"><span data-stu-id="163c3-102">Names of Type Members</span></span>
<span data-ttu-id="163c3-103">Typy składowe są elementami członkowskimi: metodami, właściwościami, zdarzeniami, konstruktorami i polami.</span><span class="sxs-lookup"><span data-stu-id="163c3-103">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="163c3-104">W poniższych sekcjach opisano wskazówki dotyczące nazewnictwa elementów członkowskich typu.</span><span class="sxs-lookup"><span data-stu-id="163c3-104">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="163c3-105">Nazwy metod</span><span class="sxs-lookup"><span data-stu-id="163c3-105">Names of Methods</span></span>
 <span data-ttu-id="163c3-106">Ponieważ metody są metodą podjęcia działania, wskazówki dotyczące projektowania wymagają, aby nazwy metod były czasownikami lub wyrażeniami czasownikowymi.</span><span class="sxs-lookup"><span data-stu-id="163c3-106">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="163c3-107">Poniższe wytyczne umożliwiają również odróżnianie nazw metod od nazw właściwości i typów, które są frazami rzeczownikmi lub przymiotnikami.</span><span class="sxs-lookup"><span data-stu-id="163c3-107">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="163c3-108">✔️ NALEŻY nadać metodom nazwy, które są czasownikami lub czasownikami zleceń.</span><span class="sxs-lookup"><span data-stu-id="163c3-108">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="163c3-109">Nazwy właściwości</span><span class="sxs-lookup"><span data-stu-id="163c3-109">Names of Properties</span></span>
 <span data-ttu-id="163c3-110">W przeciwieństwie do innych elementów członkowskich, właściwości powinny zawierać frazę rzeczowników lub nazwy przymiotników.</span><span class="sxs-lookup"><span data-stu-id="163c3-110">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="163c3-111">Oznacza to, że Właściwość odwołuje się do danych, a nazwa właściwości odzwierciedla to.</span><span class="sxs-lookup"><span data-stu-id="163c3-111">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="163c3-112">PascalCasing jest zawsze używana dla nazw właściwości.</span><span class="sxs-lookup"><span data-stu-id="163c3-112">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="163c3-113">✔️ Właściwości nazwy przy użyciu rzeczownika, frazy rzeczowników lub przymiotniku.</span><span class="sxs-lookup"><span data-stu-id="163c3-113">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="163c3-114">❌ nie mają właściwości, które pasują do nazwy metod "Get", tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="163c3-114">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="163c3-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="163c3-115">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="163c3-116">Ten wzorzec zazwyczaj wskazuje, że właściwość powinna być w rzeczywistości metodą.</span><span class="sxs-lookup"><span data-stu-id="163c3-116">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="163c3-117">✔️ DO właściwości kolekcji nazw z frazą w liczbie mnogiej opisującą elementy w kolekcji, zamiast używać pojedynczej frazy, a po niej "list" lub "Collection".</span><span class="sxs-lookup"><span data-stu-id="163c3-117">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="163c3-118">✔️ NALEŻY nazwać właściwości logiczne przy użyciu potwierdzenia (`CanSeek` zamiast `CantSeek`).</span><span class="sxs-lookup"><span data-stu-id="163c3-118">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="163c3-119">Opcjonalnie można również prefiksować właściwości logiczne z "is", "może" lub "ma", ale tylko wtedy, gdy dodaje wartość.</span><span class="sxs-lookup"><span data-stu-id="163c3-119">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="163c3-120">✔️ ROZWAŻYĆ nadanie właściwości takiej samej nazwy jak jej typ.</span><span class="sxs-lookup"><span data-stu-id="163c3-120">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="163c3-121">Na przykład następująca Właściwość prawidłowo pobiera i ustawia wartość wyliczenia o nazwie `Color`, więc właściwość ma nazwę `Color`:</span><span class="sxs-lookup"><span data-stu-id="163c3-121">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="163c3-122">Nazwy zdarzeń</span><span class="sxs-lookup"><span data-stu-id="163c3-122">Names of Events</span></span>
 <span data-ttu-id="163c3-123">Zdarzenia zawsze odwołują się do niektórych akcji, takich, które są wykonywane lub takie, które wystąpiły.</span><span class="sxs-lookup"><span data-stu-id="163c3-123">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="163c3-124">W związku z tym, podobnie jak w przypadku metod, zdarzenia są nazwane przy użyciu czasowników, a w celu wskazania czasu, gdy zdarzenie jest zgłaszane, używana jest wartość zlecenia.</span><span class="sxs-lookup"><span data-stu-id="163c3-124">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="163c3-125">✔️ NALEŻY nazwać zdarzenia za pomocą czasownika lub wyrażenia orzeczenia.</span><span class="sxs-lookup"><span data-stu-id="163c3-125">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="163c3-126">Przykłady obejmują `Clicked`, `Painting`, `DroppedDown`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="163c3-126">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="163c3-127">✔️ NALEŻY udzielić nazw zdarzeń z koncepcją przed i po, przy użyciu obecnych i ostatnich dziesiątek.</span><span class="sxs-lookup"><span data-stu-id="163c3-127">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="163c3-128">Na przykład zdarzenie zamykające wywoływane przed zamknięciem okna powinno być wywoływane `Closing`, a jeden, który jest wywoływany po zamknięciu okna, zostanie wywołany `Closed`.</span><span class="sxs-lookup"><span data-stu-id="163c3-128">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="163c3-129">❌ nie używać prefiksów "Before" lub "After", aby wskazać zdarzenia przed i po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="163c3-129">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="163c3-130">Użyj obecnych i ostatnich dziesiątek tak samo, jak zostało to opisane.</span><span class="sxs-lookup"><span data-stu-id="163c3-130">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="163c3-131">✔️ obsługi zdarzeń nazw (delegatów używanych jako typy zdarzeń) przy użyciu sufiksu "EventHandler", jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="163c3-131">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="163c3-132">✔️ należy używać dwóch parametrów o nazwach `sender` i `e` w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="163c3-132">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="163c3-133">Parametr Sender reprezentuje obiekt, który spowodował zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="163c3-133">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="163c3-134">Parametr nadawcy jest zazwyczaj typu `object`, nawet jeśli można użyć bardziej określonego typu.</span><span class="sxs-lookup"><span data-stu-id="163c3-134">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="163c3-135">✔️ NALEŻY nazwać klasy argumentów zdarzeń z sufiksem "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="163c3-135">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="163c3-136">Nazwy pól</span><span class="sxs-lookup"><span data-stu-id="163c3-136">Names of Fields</span></span>
 <span data-ttu-id="163c3-137">Wskazówki dotyczące nazewnictwa pól mają zastosowanie do statycznych pól publicznych i chronionych.</span><span class="sxs-lookup"><span data-stu-id="163c3-137">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="163c3-138">Pola wewnętrzne i prywatne nie są objęte wskazówkami, a pola Public lub Protected instance są niedozwolone w [wytycznych dotyczących projektowania elementu członkowskiego](../../../docs/standard/design-guidelines/member.md).</span><span class="sxs-lookup"><span data-stu-id="163c3-138">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](../../../docs/standard/design-guidelines/member.md).</span></span>

 <span data-ttu-id="163c3-139">✔️ używać PascalCasing w nazwach pól.</span><span class="sxs-lookup"><span data-stu-id="163c3-139">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="163c3-140">✔️ nazwy pól przy użyciu rzeczownika, frazy rzeczowników lub przymiotniku.</span><span class="sxs-lookup"><span data-stu-id="163c3-140">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="163c3-141">❌ nie należy używać prefiksu dla nazw pól.</span><span class="sxs-lookup"><span data-stu-id="163c3-141">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="163c3-142">Na przykład nie umożliwia "g_" lub "s_" oznaczają pola statyczne.</span><span class="sxs-lookup"><span data-stu-id="163c3-142">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="163c3-143">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="163c3-143">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="163c3-144">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="163c3-144">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="163c3-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="163c3-145">See also</span></span>

- [<span data-ttu-id="163c3-146">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="163c3-146">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="163c3-147">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="163c3-147">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
