---
title: Nazwy klas, struktur i interfejsów
description: Skorzystaj z tych wskazówek dotyczących nazewnictwa klas, struktur i interfejsów w ramach wytycznych dotyczących projektowania bibliotek, które zwiększają i współdziałają z bibliotekami platformy .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: b9de9329cc8e1bfc47a46523c7119bb3b2c244d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290217"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="7a175-103">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="7a175-103">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="7a175-104">Poniższe wskazówki dotyczące nazewnictwa mają zastosowanie do ogólnego nazewnictwa typów.</span><span class="sxs-lookup"><span data-stu-id="7a175-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="7a175-105">✔️ DO nazw klas i struktur z rzeczownikami lub rzeczownikami, za pomocą PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="7a175-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="7a175-106">Spowoduje to odróżnienie nazw typów od metod, które są nazywane wyrażeniami czasownik.</span><span class="sxs-lookup"><span data-stu-id="7a175-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="7a175-107">✔️ DO interfejsów nazw przy użyciu fraz przymiotników lub od czasu do czas z rzeczownikami lub frazami rzeczowniknymi.</span><span class="sxs-lookup"><span data-stu-id="7a175-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="7a175-108">Rzeczowniki i frazy rzeczowników powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.</span><span class="sxs-lookup"><span data-stu-id="7a175-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="7a175-109">❌NIE należy podawać nazw klas jako prefiksu (np. "C").</span><span class="sxs-lookup"><span data-stu-id="7a175-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="7a175-110">✔️ Rozważ zakończenie nazwy klas pochodnych o nazwie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="7a175-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="7a175-111">Jest to bardzo czytelne i jasno wyjaśniono relację.</span><span class="sxs-lookup"><span data-stu-id="7a175-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="7a175-112">Przykłady tego kodu to: `ArgumentOutOfRangeException` , który jest rodzajem `Exception` , i `SerializableAttribute` , który jest rodzajem `Attribute` .</span><span class="sxs-lookup"><span data-stu-id="7a175-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="7a175-113">Jednak ważne jest, aby użyć odpowiednich orzeczeń w zastosowaniu niniejszych wytycznych; na przykład `Button` Klasa jest rodzajem `Control` zdarzenia, chociaż `Control` nie pojawia się w jego nazwie.</span><span class="sxs-lookup"><span data-stu-id="7a175-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="7a175-114">✔️ NALEŻY prefiksować nazwy interfejsów z literą I, aby wskazać, że typ jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="7a175-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="7a175-115">Na przykład `IComponent` : (rzeczownik opisowy), `ICustomAttributeProvider` (wyrażenie rzeczownik) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7a175-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="7a175-116">Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.</span><span class="sxs-lookup"><span data-stu-id="7a175-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="7a175-117">✔️ Upewnij się, że nazwy różnią się tylko prefiksem "I" w nazwie interfejsu podczas definiowania pary interfejsów klasy, w których Klasa jest implementacją standardową interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7a175-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="7a175-118">Nazwy parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="7a175-118">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="7a175-119">Typy ogólne zostały dodane do .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="7a175-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="7a175-120">Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="7a175-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="7a175-121">✔️ nazywają ogólne parametry typu z nazwami opisowymi, chyba że jednoliterowa nazwa nie jest całkowicie oczywista, a nazwa opisowa nie będzie dodawać wartości.</span><span class="sxs-lookup"><span data-stu-id="7a175-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="7a175-122">✔️ ROZWAŻYĆ użycie `T` jako nazwy parametru typu dla typów z jednym jednoliterowym parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="7a175-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="7a175-123">✔️ Wykonaj prefiks nazw parametrów typu opisowego z `T` .</span><span class="sxs-lookup"><span data-stu-id="7a175-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="7a175-124">✔️ ROZWAŻYĆ wskazanie ograniczeń umieszczanych na parametrze typu w nazwie parametru.</span><span class="sxs-lookup"><span data-stu-id="7a175-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="7a175-125">Na przykład parametr ograniczony do `ISession` może być wywoływany `TSession` .</span><span class="sxs-lookup"><span data-stu-id="7a175-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="7a175-126">Nazwy typów wspólnych</span><span class="sxs-lookup"><span data-stu-id="7a175-126">Names of Common Types</span></span>
 <span data-ttu-id="7a175-127">✔️ Postępuj zgodnie z wytycznymi opisanymi w poniższej tabeli podczas nazewnictwa typów pochodnych lub implementacji niektórych typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a175-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="7a175-128">Typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="7a175-128">Base Type</span></span>|<span data-ttu-id="7a175-129">Wytyczne typu pochodnego/implementującego</span><span class="sxs-lookup"><span data-stu-id="7a175-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="7a175-130">✔️ dodać sufiks "Attribute" do nazw klas atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7a175-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="7a175-131">✔️ Dodaj sufiks "EventHandler" do nazw delegatów używanych w zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="7a175-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="7a175-132">✔️ Dodaj sufiks "wywołanie zwrotne" do nazw delegatów innych niż te używane jako programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7a175-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="7a175-133">❌Nie dodawaj sufiksu "delegat" do delegata.</span><span class="sxs-lookup"><span data-stu-id="7a175-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="7a175-134">✔️ dodać sufiks "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="7a175-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="7a175-135">❌NIE pochodzą od tej klasy; Zamiast tego należy użyć słowa kluczowego obsługiwanego przez język; na przykład, w języku C#, użyj `enum` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7a175-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="7a175-136">❌NIE należy dodawać sufiksu "enum" ani "flag".</span><span class="sxs-lookup"><span data-stu-id="7a175-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="7a175-137">✔️ Dodaj sufiks "Exception".</span><span class="sxs-lookup"><span data-stu-id="7a175-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="7a175-138">✔️ dodać sufiks "dictionary".</span><span class="sxs-lookup"><span data-stu-id="7a175-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="7a175-139">Należy pamiętać, że `IDictionary` jest to konkretny typ kolekcji, ale wskazówki te mają pierwszeństwo przed bardziej ogólnymi wskazówkami dotyczącymi kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7a175-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="7a175-140">✔️ dodać sufiks "Kolekcja".</span><span class="sxs-lookup"><span data-stu-id="7a175-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="7a175-141">✔️ dodać sufiks "Stream".</span><span class="sxs-lookup"><span data-stu-id="7a175-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="7a175-142">✔️ dodać sufiks "uprawnienie".</span><span class="sxs-lookup"><span data-stu-id="7a175-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="7a175-143">Wyliczanie nazw</span><span class="sxs-lookup"><span data-stu-id="7a175-143">Naming Enumerations</span></span>
 <span data-ttu-id="7a175-144">Nazwy typów wyliczeniowych (nazywane również wyliczeniami) ogólnie powinny być zgodne ze standardowymi regułami nazewnictwa typów (PascalCasing itp.).</span><span class="sxs-lookup"><span data-stu-id="7a175-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="7a175-145">Istnieją jednak dodatkowe wytyczne, które dotyczą wyłącznie wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="7a175-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="7a175-146">✔️ do wyliczenia należy używać pojedynczej nazwy typu, chyba że jej wartości są polami bitowymi.</span><span class="sxs-lookup"><span data-stu-id="7a175-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="7a175-147">✔️ należy używać nazwy typu w liczbie mnogiej dla wyliczenia z polami bitowymi jako wartości, nazywane również flagami enum.</span><span class="sxs-lookup"><span data-stu-id="7a175-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="7a175-148">❌NIE używaj sufiksu "enum" w nazwach typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="7a175-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="7a175-149">❌NIE używaj sufiksów "flag" ani "flags" w nazwach typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="7a175-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="7a175-150">❌NIE należy używać prefiksu dla nazw wartości wyliczenia (np. "AD" dla wyliczeń ADO, "RTF" dla tekstu sformatowanego RTF itp.).</span><span class="sxs-lookup"><span data-stu-id="7a175-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="7a175-151">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7a175-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7a175-152">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="7a175-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7a175-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7a175-153">See also</span></span>

- [<span data-ttu-id="7a175-154">Wskazówki dotyczące projektowania struktury</span><span class="sxs-lookup"><span data-stu-id="7a175-154">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="7a175-155">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="7a175-155">Naming Guidelines</span></span>](naming-guidelines.md)
