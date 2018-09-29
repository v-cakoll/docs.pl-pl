---
title: Nazwy klas, struktur i interfejsów
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c56f840bc5ebd5070c9b686384751acab3f0203
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454331"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="3e9fa-102">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="3e9fa-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="3e9fa-103">Wskazówkami nazewnictwa, które należy wykonać dotyczą nazewnictwa typ ogólny.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="3e9fa-104">**✓ DO** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="3e9fa-105">Nazwy typów to odróżnia od metody, które są nazywane oraz oznaczenia zlecenie.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="3e9fa-106">**✓ DO** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="3e9fa-107">Rzeczowniki i fraz rzeczownik powinny być rzadko używane i może wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="3e9fa-108">**X DO NOT** nadaj nazwę klasy prefiksu (np. "C").</span><span class="sxs-lookup"><span data-stu-id="3e9fa-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="3e9fa-109">**✓ CONSIDER** kończy nazwę klasy o nazwie klasy podstawowej pochodne.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="3e9fa-110">To jest bardzo czytelny i wyraźnie opisano relację.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="3e9fa-111">Oto kilka przykładów tego kodu: `ArgumentOutOfRangeException`, który jest rodzajem z `Exception`, i `SerializableAttribute`, co jest rodzajem z `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="3e9fa-112">Jednak warto użyć uzasadnione orzeczenia stosowania ta wytyczna; na przykład `Button` klasy jest rodzajem elementu `Control` zdarzeń, mimo że `Control` nie pojawia się w jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="3e9fa-113">**✓ DO** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="3e9fa-114">Na przykład `IComponent` (opisowego rzeczownika) `ICustomAttributeProvider` (rzeczownik oznaczenie), i `IPersistable` (przymiotnik) są nazwami odpowiedniego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="3e9fa-115">Podobnie jak w przypadku innych nazwami typów, unikaj skrótów.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="3e9fa-116">**✓ DO** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="3e9fa-117">Nazwy parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="3e9fa-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="3e9fa-118">Typy ogólne zostały dodane do programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="3e9fa-119">Wprowadzonej nowego rodzaju identyfikatora zwanego *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="3e9fa-120">**✓ DO** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="3e9fa-121">**✓ CONSIDER** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="3e9fa-122">**✓ DO** prefiksu nazwy parametrów typu opisową z `T`.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="3e9fa-123">**✓ CONSIDER** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="3e9fa-124">Na przykład parametr ograniczone do `ISession` może być wywoływana `TSession`.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="3e9fa-125">Nazwy typów wspólnych</span><span class="sxs-lookup"><span data-stu-id="3e9fa-125">Names of Common Types</span></span>  
 <span data-ttu-id="3e9fa-126">**✓ DO** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="3e9fa-127">Typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="3e9fa-127">Base Type</span></span>|<span data-ttu-id="3e9fa-128">Pochodne Implementowanie wskazówek dotyczących typów</span><span class="sxs-lookup"><span data-stu-id="3e9fa-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="3e9fa-129">**✓ DO** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="3e9fa-130">**✓ DO** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="3e9fa-131">**✓ DO** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="3e9fa-132">**X DO NOT** dodać sufiks "Delegowanie" do delegata.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="3e9fa-133">**✓ DO** dodać sufiks "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="3e9fa-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="3e9fa-134">**X DO NOT** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="3e9fa-135">**X DO NOT** dodać sufiks "Enum" lub "Flaga".</span><span class="sxs-lookup"><span data-stu-id="3e9fa-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="3e9fa-136">**✓ DO** dodać sufiks "Wyjątku."</span><span class="sxs-lookup"><span data-stu-id="3e9fa-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="3e9fa-137">**✓ DO** dodać sufiks "Słownik".</span><span class="sxs-lookup"><span data-stu-id="3e9fa-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="3e9fa-138">Należy pamiętać, że `IDictionary` jest określonego typu kolekcji, ale ta wytyczna ma pierwszeństwo przed bardziej ogólne wytyczne kolekcji, który następuje po.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="3e9fa-139">**✓ DO** dodać sufiksem "Collection".</span><span class="sxs-lookup"><span data-stu-id="3e9fa-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="3e9fa-140">**✓ DO** dodać sufiks "Strumień".</span><span class="sxs-lookup"><span data-stu-id="3e9fa-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="3e9fa-141">**✓ DO** dodać sufiks "Uprawnienia."</span><span class="sxs-lookup"><span data-stu-id="3e9fa-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="3e9fa-142">Nazwy wyliczeń</span><span class="sxs-lookup"><span data-stu-id="3e9fa-142">Naming Enumerations</span></span>  
 <span data-ttu-id="3e9fa-143">Ogólnie rzecz biorąc nazwy Typy wyliczeniowe (nazywane również Typy wyliczeniowe) powinien być zgodny standardowe reguły nazewnictwa typu (PascalCasing itp.).</span><span class="sxs-lookup"><span data-stu-id="3e9fa-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="3e9fa-144">Jednakże istnieją dodatkowe wskazówki, które mają zastosowanie szczególnie w przypadku typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="3e9fa-145">**✓ DO** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="3e9fa-146">**✓ DO** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="3e9fa-147">**X DO NOT** Użyj sufiksu "Enum" w nazwach typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="3e9fa-148">**X DO NOT** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="3e9fa-149">**X DO NOT** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.</span><span class="sxs-lookup"><span data-stu-id="3e9fa-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="3e9fa-150">*Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="3e9fa-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3e9fa-151">*Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="3e9fa-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e9fa-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e9fa-152">See also</span></span>

- [<span data-ttu-id="3e9fa-153">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="3e9fa-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="3e9fa-154">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="3e9fa-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
