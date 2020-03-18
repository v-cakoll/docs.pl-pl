---
title: Nazwy klas, struktur i interfejsów
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
ms.openlocfilehash: 2c528348c0e84037a80df9797c56f03b51c73adc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400597"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="cbada-102">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="cbada-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="cbada-103">Poniższe wskazówki dotyczące nazewnictwa dotyczą nazewnictwa typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="cbada-103">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="cbada-104">✔️ do klas nazw i struktur z rzeczownikami lub frazami rzeczownikowymi, za pomocą PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="cbada-104">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="cbada-105">Rozróżnia nazwy typów od metod, które są nazywane frazami czasownikowymi.</span><span class="sxs-lookup"><span data-stu-id="cbada-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="cbada-106">✔️ do interfejsów nazw z przymiotnikami lub od czasu do czasu z rzeczownikami lub frazami rzeczowników.</span><span class="sxs-lookup"><span data-stu-id="cbada-106">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="cbada-107">Rzeczowniki i rzeczowniki powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.</span><span class="sxs-lookup"><span data-stu-id="cbada-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="cbada-108">❌NIE należy podawać nazw klas prefiks (np.</span><span class="sxs-lookup"><span data-stu-id="cbada-108">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="cbada-109">✔️ ZASTANÓW SIĘ, kończąc nazwę klas pochodnych nazwą klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="cbada-109">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="cbada-110">Jest to bardzo czytelne i wyraźnie wyjaśnia związek.</span><span class="sxs-lookup"><span data-stu-id="cbada-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="cbada-111">Niektóre przykłady tego w kodzie `ArgumentOutOfRangeException`to: , `Exception`który `SerializableAttribute`jest rodzajem `Attribute`, i , który jest rodzajem .</span><span class="sxs-lookup"><span data-stu-id="cbada-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="cbada-112">Jednakże ważne jest, aby stosować rozsądną ocenę przy stosowaniu niniejszych wytycznych; na przykład `Button` klasa jest rodzajem `Control` zdarzenia, chociaż `Control` nie pojawia się w jego nazwie.</span><span class="sxs-lookup"><span data-stu-id="cbada-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="cbada-113">✔️ nazwy interfejsu prefiksu DO z literą I, aby wskazać, że typ jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="cbada-113">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="cbada-114">Na przykład `IComponent` (rzeczownik opisowy), `ICustomAttributeProvider` (fraza rzeczownikowa) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cbada-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="cbada-115">Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.</span><span class="sxs-lookup"><span data-stu-id="cbada-115">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="cbada-116">✔️ upewnij się, że nazwy różnią się tylko przez prefiks "I" na nazwę interfejsu podczas definiowania pary klasy interfejsu, gdzie klasa jest standardową implementacją interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cbada-116">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="cbada-117">Nazwy parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="cbada-117">Names of Generic Type Parameters</span></span>
 <span data-ttu-id="cbada-118">Generycznych zostały dodane do .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="cbada-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="cbada-119">Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="cbada-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="cbada-120">✔️ DO nazwa ogólnych parametrów typu z opisowymi nazwami, chyba że nazwa jednoliterowa jest całkowicie oczywista i nazwa opisowa nie doda wartości.</span><span class="sxs-lookup"><span data-stu-id="cbada-120">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="cbada-121">✔️ ZASTANÓW SIĘ, używając `T` jako nazwy parametru typu dla typów z jednym parametrem typu jednoliterowego.</span><span class="sxs-lookup"><span data-stu-id="cbada-121">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="cbada-122">✔️ DO prefiksu nazwy parametrów `T`typu opisowego z .</span><span class="sxs-lookup"><span data-stu-id="cbada-122">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="cbada-123">✔️ ROZWAŻ Wskazanie ograniczeń umieszczonych na parametrze typu w nazwie parametru.</span><span class="sxs-lookup"><span data-stu-id="cbada-123">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="cbada-124">Na przykład parametr ograniczony do `ISession` może `TSession`być wywoływana .</span><span class="sxs-lookup"><span data-stu-id="cbada-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="cbada-125">Nazwy typów wspólnych</span><span class="sxs-lookup"><span data-stu-id="cbada-125">Names of Common Types</span></span>
 <span data-ttu-id="cbada-126">✔️ wykonaj wytyczne opisane w poniższej tabeli podczas nazywania typów pochodzących z lub implementowania niektórych typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="cbada-126">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="cbada-127">Typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="cbada-127">Base Type</span></span>|<span data-ttu-id="cbada-128">Wytyczne dotyczące typu pochodnego/wykonawczego</span><span class="sxs-lookup"><span data-stu-id="cbada-128">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="cbada-129">✔️ DO dodać sufiks "Atrybut" do nazw klas atrybutów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="cbada-129">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="cbada-130">✔️ DO dodać sufiks "EventHandler" do nazw delegatów, które są używane w zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="cbada-130">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="cbada-131">✔️ DO dodać sufiks "Wywołanie zwrotu" do nazw delegatów innych niż te używane jako programy obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="cbada-131">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="cbada-132">❌NIE dodawaj sufiksu "Delegować" do pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="cbada-132">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="cbada-133">✔️ DO dodać sufiks "EventArgs".</span><span class="sxs-lookup"><span data-stu-id="cbada-133">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="cbada-134">❌NIE wywodzić z tej klasy; zamiast tego użyj słowa kluczowego obsługiwanego przez twój język; na przykład w języku `enum` C#, użyj słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="cbada-134">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="cbada-135">❌NIE dodawaj sufiksu "Wyliczenie" ani "Flaga".</span><span class="sxs-lookup"><span data-stu-id="cbada-135">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="cbada-136">✔️ DO dodać sufiks "Wyjątek".</span><span class="sxs-lookup"><span data-stu-id="cbada-136">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="cbada-137">✔️ DO dodać sufiks "Słownik".</span><span class="sxs-lookup"><span data-stu-id="cbada-137">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="cbada-138">Należy `IDictionary` zauważyć, że jest to określony typ kolekcji, ale ta wskazówka ma pierwszeństwo przed bardziej ogólne wskazówki kolekcje, które następuje.</span><span class="sxs-lookup"><span data-stu-id="cbada-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="cbada-139">✔️ DO dodać sufiks "Kolekcja".</span><span class="sxs-lookup"><span data-stu-id="cbada-139">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="cbada-140">✔️ DO dodać przyrostek "Strumień".</span><span class="sxs-lookup"><span data-stu-id="cbada-140">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="cbada-141">✔️ DO dodać sufiks "Uprawnienie".</span><span class="sxs-lookup"><span data-stu-id="cbada-141">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="cbada-142">Nazewnictwo Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="cbada-142">Naming Enumerations</span></span>
 <span data-ttu-id="cbada-143">Nazwy typów wyliczenia (nazywane również wyliczeniami) w ogóle powinny być zgodne ze standardowymi regułami nazewnictwa typu (PascalCasing itp.).</span><span class="sxs-lookup"><span data-stu-id="cbada-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="cbada-144">Istnieją jednak dodatkowe wytyczne, które mają zastosowanie specjalnie do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cbada-144">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="cbada-145">✔️ do używania nazwy typu pojedynczego dla wyliczenia, chyba że jego wartości są pola bitowe.</span><span class="sxs-lookup"><span data-stu-id="cbada-145">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="cbada-146">✔️ DO używać nazwy typu liczby mnogiej dla wyliczenia z pól bitowych jako wartości, nazywane również flagi wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cbada-146">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="cbada-147">❌NIE należy używać sufiksu "Wyliczenie" w nazwach typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cbada-147">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="cbada-148">❌NIE należy używać sufiksów "Flag" ani "Flags" w nazwach typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="cbada-148">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="cbada-149">❌NIE należy używać prefiksu w nazwach wartości wyliczenia (np. "ad" dla wyliczeń ADO, "rtf" dla wyliczeń tekstu sformatnego itp.).</span><span class="sxs-lookup"><span data-stu-id="cbada-149">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="cbada-150">*Części © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="cbada-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="cbada-151">*Przedruk za zgodą Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms i Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) autorstwa Krzysztofa Cwaliny i Brada Abramsa, opublikowane 22 października 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="cbada-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="cbada-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbada-152">See also</span></span>

- [<span data-ttu-id="cbada-153">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="cbada-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="cbada-154">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="cbada-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
