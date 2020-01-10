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
ms.openlocfilehash: 96d9904af0106d797c9fc5199bda76da53874451
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709247"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="049e0-102">Nazwy klas, struktur i interfejsów</span><span class="sxs-lookup"><span data-stu-id="049e0-102">Names of Classes, Structs, and Interfaces</span></span>
<span data-ttu-id="049e0-103">Poniższe wskazówki dotyczące nazewnictwa mają zastosowanie do ogólnego nazewnictwa typów.</span><span class="sxs-lookup"><span data-stu-id="049e0-103">The naming guidelines that follow apply to general type naming.</span></span>  
  
 <span data-ttu-id="049e0-104">**✓ DO** nazwy klas i struktur rzeczowniki lub fraz rzeczownik, przy użyciu PascalCasing.</span><span class="sxs-lookup"><span data-stu-id="049e0-104">**✓ DO** name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>  
  
 <span data-ttu-id="049e0-105">Spowoduje to odróżnienie nazw typów od metod, które są nazywane wyrażeniami czasownik.</span><span class="sxs-lookup"><span data-stu-id="049e0-105">This distinguishes type names from methods, which are named with verb phrases.</span></span>  
  
 <span data-ttu-id="049e0-106">**✓ DO** nazwy interfejsów przymiotników fraz lub czasami rzeczowniki ani fraz rzeczownik.</span><span class="sxs-lookup"><span data-stu-id="049e0-106">**✓ DO** name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="049e0-107">Rzeczowniki i frazy rzeczowników powinny być używane rzadko i mogą wskazywać, że typ powinien być klasą abstrakcyjną, a nie interfejsem.</span><span class="sxs-lookup"><span data-stu-id="049e0-107">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>  
  
 <span data-ttu-id="049e0-108">**X DO NOT** nadaj nazwę klasy prefiksu (np. "C").</span><span class="sxs-lookup"><span data-stu-id="049e0-108">**X DO NOT** give class names a prefix (e.g., "C").</span></span>  
  
 <span data-ttu-id="049e0-109">**✓ CONSIDER** kończy nazwę klasy o nazwie klasy podstawowej pochodne.</span><span class="sxs-lookup"><span data-stu-id="049e0-109">**✓ CONSIDER** ending the name of derived classes with the name of the base class.</span></span>  
  
 <span data-ttu-id="049e0-110">Jest to bardzo czytelne i jasno wyjaśniono relację.</span><span class="sxs-lookup"><span data-stu-id="049e0-110">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="049e0-111">Przykładami tego kodu jest: `ArgumentOutOfRangeException`, który jest rodzajem `Exception`i `SerializableAttribute`, który jest rodzajem `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="049e0-111">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="049e0-112">Jednak ważne jest, aby użyć odpowiednich orzeczeń w zastosowaniu niniejszych wytycznych; na przykład Klasa `Button` jest rodzajem zdarzenia `Control`, chociaż `Control` nie pojawia się w jego nazwie.</span><span class="sxs-lookup"><span data-stu-id="049e0-112">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>  
  
 <span data-ttu-id="049e0-113">**✓ DO** interfejsu prefiksu nazwy z literą I, aby wskazać, że typ jest interfejsem.</span><span class="sxs-lookup"><span data-stu-id="049e0-113">**✓ DO** prefix interface names with the letter I, to indicate that the type is an interface.</span></span>  
  
 <span data-ttu-id="049e0-114">Na przykład, `IComponent` (rzeczownik opisowy), `ICustomAttributeProvider` (phrase rzeczownik) i `IPersistable` (przymiotnik) są odpowiednimi nazwami interfejsów.</span><span class="sxs-lookup"><span data-stu-id="049e0-114">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="049e0-115">Podobnie jak w przypadku innych nazw typów, należy unikać skrótów.</span><span class="sxs-lookup"><span data-stu-id="049e0-115">As with other type names, avoid abbreviations.</span></span>  
  
 <span data-ttu-id="049e0-116">**✓ DO** upewnij się, że nazwy są różne tylko przez "I" prefiksu nazwy interfejsu podczas definiowania parę klasy — interfejs klasy w przypadku standardowej implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="049e0-116">**✓ DO** ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>  
  
## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="049e0-117">Nazwy parametrów typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="049e0-117">Names of Generic Type Parameters</span></span>  
 <span data-ttu-id="049e0-118">Typy ogólne zostały dodane do .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="049e0-118">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="049e0-119">Funkcja wprowadziła nowy rodzaj identyfikatora o nazwie *parametr typu*.</span><span class="sxs-lookup"><span data-stu-id="049e0-119">The feature introduced a new kind of identifier called *type parameter*.</span></span>  
  
 <span data-ttu-id="049e0-120">**✓ DO** nazwa parametry typu ogólnego z nazw opisowych, chyba że jednym litera jest całkowicie oczywiste i nazwę opisową nie może dodać wartość.</span><span class="sxs-lookup"><span data-stu-id="049e0-120">**✓ DO** name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>  
  
 <span data-ttu-id="049e0-121">**✓ CONSIDER** przy użyciu `T` jako nazwę parametru typu dla typów z jednym parametrem litery jednego typu.</span><span class="sxs-lookup"><span data-stu-id="049e0-121">**✓ CONSIDER** using `T` as the type parameter name for types with one single-letter type parameter.</span></span>  
  
```csharp  
public int IComparer<T> { ... }  
public delegate bool Predicate<T>(T item);  
public struct Nullable<T> where T:struct { ... }  
```  
  
 <span data-ttu-id="049e0-122">**✓ DO** prefiksu nazwy parametrów typu opisową z `T`.</span><span class="sxs-lookup"><span data-stu-id="049e0-122">**✓ DO** prefix descriptive type parameter names with `T`.</span></span>  
  
```csharp  
public interface ISessionChannel<TSession> where TSession : ISession {  
    TSession Session { get; }  
}  
```  
  
 <span data-ttu-id="049e0-123">**✓ CONSIDER** wskazujący ograniczenia umieścić w parametrze typu nazwy parametru.</span><span class="sxs-lookup"><span data-stu-id="049e0-123">**✓ CONSIDER** indicating constraints placed on a type parameter in the name of the parameter.</span></span>  
  
 <span data-ttu-id="049e0-124">Na przykład parametr ograniczony do `ISession` może być wywołany `TSession`.</span><span class="sxs-lookup"><span data-stu-id="049e0-124">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>  
  
## <a name="names-of-common-types"></a><span data-ttu-id="049e0-125">Nazwy typów wspólnych</span><span class="sxs-lookup"><span data-stu-id="049e0-125">Names of Common Types</span></span>  
 <span data-ttu-id="049e0-126">**✓ DO** postępuj zgodnie z wytycznymi opisane w poniższej tabeli w nazwach typów pochodnych lub wykonania pewnych typów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="049e0-126">**✓ DO** follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>  
  
|<span data-ttu-id="049e0-127">Typ podstawowy</span><span class="sxs-lookup"><span data-stu-id="049e0-127">Base Type</span></span>|<span data-ttu-id="049e0-128">Wytyczne typu pochodnego/implementującego</span><span class="sxs-lookup"><span data-stu-id="049e0-128">Derived/Implementing Type Guideline</span></span>|  
|---------------|------------------------------------------|  
|`System.Attribute`|<span data-ttu-id="049e0-129">**✓ DO** dodać sufiks "Atrybutu" do nazwy klasy atrybutu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="049e0-129">**✓ DO** add the suffix "Attribute" to names of custom attribute classes.</span></span>|  
|`System.Delegate`|<span data-ttu-id="049e0-130">**✓ DO** dodać sufiks "EventHandler" do nazwy obiektów delegowanych, które są używane w zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="049e0-130">**✓ DO** add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="049e0-131">**✓ DO** dodać sufiks "Wywołania zwrotnego" do nazwy obiektów delegowanych innych niż te używane jako procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="049e0-131">**✓ DO** add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="049e0-132">**X DO NOT** dodać sufiks "Delegowanie" do delegata.</span><span class="sxs-lookup"><span data-stu-id="049e0-132">**X DO NOT** add the suffix "Delegate" to a delegate.</span></span>|  
|`System.EventArgs`|<span data-ttu-id="049e0-133">**✓ DO** dodać sufiks "EventArgs."</span><span class="sxs-lookup"><span data-stu-id="049e0-133">**✓ DO** add the suffix "EventArgs."</span></span>|  
|`System.Enum`|<span data-ttu-id="049e0-134">**X DO NOT** pochodzi od tej klasy; użyj słowa kluczowego zamiast obsługiwane przez język; na przykład w języku C#, użyj `enum` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="049e0-134">**X DO NOT** derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="049e0-135">**X DO NOT** dodać sufiks "Enum" lub "Flaga".</span><span class="sxs-lookup"><span data-stu-id="049e0-135">**X DO NOT** add the suffix "Enum" or "Flag."</span></span>|  
|`System.Exception`|<span data-ttu-id="049e0-136">**✓ DO** dodać sufiks "Wyjątku."</span><span class="sxs-lookup"><span data-stu-id="049e0-136">**✓ DO** add the suffix "Exception."</span></span>|  
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="049e0-137">**✓ DO** dodać sufiks "Słownik".</span><span class="sxs-lookup"><span data-stu-id="049e0-137">**✓ DO** add the suffix "Dictionary."</span></span> <span data-ttu-id="049e0-138">Należy zauważyć, że `IDictionary` jest określonym typem kolekcji, ale wskazówki te mają pierwszeństwo przed bardziej ogólnymi wskazówkami dotyczącymi kolekcji.</span><span class="sxs-lookup"><span data-stu-id="049e0-138">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|  
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="049e0-139">**✓ DO** dodać sufiksem "Collection".</span><span class="sxs-lookup"><span data-stu-id="049e0-139">**✓ DO** add the suffix "Collection."</span></span>|  
|`System.IO.Stream`|<span data-ttu-id="049e0-140">**✓ DO** dodać sufiks "Strumień".</span><span class="sxs-lookup"><span data-stu-id="049e0-140">**✓ DO** add the suffix "Stream."</span></span>|  
|`CodeAccessPermission IPermission`|<span data-ttu-id="049e0-141">**✓ DO** dodać sufiks "Uprawnienia."</span><span class="sxs-lookup"><span data-stu-id="049e0-141">**✓ DO** add the suffix "Permission."</span></span>|  
  
## <a name="naming-enumerations"></a><span data-ttu-id="049e0-142">Wyliczanie nazw</span><span class="sxs-lookup"><span data-stu-id="049e0-142">Naming Enumerations</span></span>  
 <span data-ttu-id="049e0-143">Nazwy typów wyliczeniowych (nazywane również wyliczeniami) ogólnie powinny być zgodne ze standardowymi regułami nazewnictwa typów (PascalCasing itp.).</span><span class="sxs-lookup"><span data-stu-id="049e0-143">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="049e0-144">Istnieją jednak dodatkowe wytyczne, które dotyczą wyłącznie wyliczeń.</span><span class="sxs-lookup"><span data-stu-id="049e0-144">However, there are additional guidelines that apply specifically to enums.</span></span>  
  
 <span data-ttu-id="049e0-145">**✓ DO** Użyj nazwy typu pojedynczej wyliczania, chyba że jego wartości pól bitowych.</span><span class="sxs-lookup"><span data-stu-id="049e0-145">**✓ DO** use a singular type name for an enumeration unless its values are bit fields.</span></span>  
  
 <span data-ttu-id="049e0-146">**✓ DO** Użyj nazwy typu w liczbie mnogiej wyliczania z pól bitowych jako wartości, nazywane również wyliczenia flag.</span><span class="sxs-lookup"><span data-stu-id="049e0-146">**✓ DO** use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>  
  
 <span data-ttu-id="049e0-147">**X DO NOT** Użyj sufiksu "Enum" w nazwach typów wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="049e0-147">**X DO NOT** use an "Enum" suffix in enum type names.</span></span>  
  
 <span data-ttu-id="049e0-148">**X DO NOT** Użyj "Flaga" lub nazwy typów, sufiksy "Flag" w elemencie enum.</span><span class="sxs-lookup"><span data-stu-id="049e0-148">**X DO NOT** use "Flag" or "Flags" suffixes in enum type names.</span></span>  
  
 <span data-ttu-id="049e0-149">**X DO NOT** Użyj prefiksu nazwy wartości wyliczenia (np. "ad" do wyliczenia obiektów ADO.), "format rtf" dla wyliczenia RTF itd.</span><span class="sxs-lookup"><span data-stu-id="049e0-149">**X DO NOT** use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>  
  
 <span data-ttu-id="049e0-150">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="049e0-150">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="049e0-151">*Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="049e0-151">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="049e0-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="049e0-152">See also</span></span>

- [<span data-ttu-id="049e0-153">Struktura — zalecenia dotyczące projektowania</span><span class="sxs-lookup"><span data-stu-id="049e0-153">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="049e0-154">Wskazówki dotyczące nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="049e0-154">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)
