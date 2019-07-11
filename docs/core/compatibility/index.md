---
title: Oceń przełomowych zmianach — .NET Core
description: Dowiedz się więcej o sposobach, w którym próbuje zachować zgodność dla deweloperów w różnych wersjach .NET platformy .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: c68a19b8b98a98bb9c64f5b9fa60b378935e6e93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736561"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="7910c-103">Oceń przełomowe zmiany w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="7910c-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="7910c-104">Całej swojej historii .NET próbował utrzymanie wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach programu .NET.</span><span class="sxs-lookup"><span data-stu-id="7910c-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="7910c-105">Ten proces jest kontynuowany prawdziwe dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7910c-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="7910c-106">Mimo że platformy .NET Core może być traktowany jako nową technologię, która jest niezależna od programu .NET Framework, dwa główne czynniki Ogranicz możliwość rozdzielić z .NET Framework .NET Core:</span><span class="sxs-lookup"><span data-stu-id="7910c-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="7910c-107">Wielu deweloperów pierwotnie opracowana albo kontynuować tworzenie aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7910c-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="7910c-108">Spójne zachowanie spełniają oczekiwane przez implementacje platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="7910c-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="7910c-109">Projekty biblioteki .NET standard umożliwia deweloperom tworzenie bibliotek, których platformą docelową, wspólnych interfejsów API udostępnionych przez oprogramowanie .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7910c-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="7910c-110">Deweloperzy oczekują, że biblioteki używane w aplikacji .NET Core powinny działać identycznie do tej samej biblioteki używane w aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7910c-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="7910c-111">Wraz z zgodność między implementacje platformy .NET deweloperów oczekują wysokiego poziomu zgodności między wersjami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7910c-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="7910c-112">W szczególności przeznaczony dla starszej wersji programu .NET Core powinien zostać uruchomiony kod bezproblemowo w nowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7910c-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="7910c-113">W rzeczywistości wielu deweloperów się spodziewać, że nowe interfejsy API znaleziony w nowo wydane wersje programu .NET Core powinny być zgodne ze wstępnymi wersjami, w których wprowadzono tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="7910c-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="7910c-114">W tym artykule przedstawiono kategorie zmiany zgodności (lub zmiany powodujące niezgodność) i sposób, w którym zespół .NET daje w wyniku zmiany w każdej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="7910c-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="7910c-115">Zrozumienie, jak zbliża się do zespołu .NET możliwych przełomowych zmian jest szczególnie przydatne dla programistów, którzy są otwieranie żądania ściągnięcia w [dotnet/corefx](https://github.com/dotnet/corefx) repozytorium GitHub, które modyfikują zachowanie istniejących interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="7910c-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="7910c-116">Dla definicji kategorii zgodności, takich jak zgodność binarną i zgodności z poprzednimi wersjami, zobacz [istotnej zmiany kategorie](categories.md).</span><span class="sxs-lookup"><span data-stu-id="7910c-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="7910c-117">Poniższe sekcje w tym artykule opisano rodzaje zmian wprowadzonych do interfejsów API platformy .NET Core i ich wpływ na zgodność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7910c-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="7910c-118">Ikona ✔️ wskazuje, że określonego rodzaju zmian jest dozwolone, ❌ wskazuje, że jest to niedozwolone, natomiast ❓ oznacza zmianę, która może być lub może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="7910c-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="7910c-119">Zmiany w tej ostatniej kategorii wymagają orzeczenia i został ocenę jak przewidywalnym oczywisty i spójne poprzednie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="7910c-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="7910c-120">Oprócz służy jako przewodnik dotyczący sposobu zmiany w bibliotekach .NET Core są oceniane, deweloperów bibliotek można również użyć tych kryteriów można ocenić zmian wprowadzonych do ich bibliotek przeznaczonych do wielu implementacji platformy .NET i wersje.</span><span class="sxs-lookup"><span data-stu-id="7910c-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="7910c-121">Modyfikacje publicznego kontraktu</span><span class="sxs-lookup"><span data-stu-id="7910c-121">Modifications to the public contract</span></span>

<span data-ttu-id="7910c-122">Zmiany w tej kategorii *zmodyfikować* publiczny obszar powierzchni typu.</span><span class="sxs-lookup"><span data-stu-id="7910c-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="7910c-123">Większość zmian w tej kategorii są niedozwolone, ponieważ mogą naruszyć *wstecznej zgodności* (możliwości aplikacji, który został opracowany przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="7910c-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="7910c-124">Types</span><span class="sxs-lookup"><span data-stu-id="7910c-124">Types</span></span>

- <span data-ttu-id="7910c-125">**✔️ Usuwanie implementację interfejsu z typu, gdy interfejs został już zaimplementowany przez typ podstawowy**</span><span class="sxs-lookup"><span data-stu-id="7910c-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="7910c-126">**Dodawanie nowej implementacji interfejsu na typ ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="7910c-127">Jest to dopuszczalne zmiany, ponieważ nie niekorzystnie wpłynąć na istniejących klientów.</span><span class="sxs-lookup"><span data-stu-id="7910c-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="7910c-128">Wszelkie zmiany typu musi działać w granicach dopuszczalne zmiany zdefiniowane w tym miejscu dla nowej implementacji pozostaje dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="7910c-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="7910c-129">Należy zachować wyjątkową ostrożność zachodzi podczas dodawania interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatora do generowania kodu lub dane, które nie mogą być używane niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="7910c-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="7910c-130">Na przykład <xref:System.Runtime.Serialization.ISerializable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7910c-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="7910c-131">**Wprowadzenie do nowej klasy ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="7910c-132">Typu mogą zostać wprowadzone do hierarchii między dwoma typami istniejących, jeśli go nie będzie żadnego wprowadzenie nowych [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) członków lub zmień semantyki oraz zachowanie istniejących typów.</span><span class="sxs-lookup"><span data-stu-id="7910c-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="7910c-133">Na przykład w programie .NET Framework 2.0 <xref:System.Data.Common.DbConnection> klasy stało się nowe klasy bazowej dla <xref:System.Data.SqlClient.SqlConnection>, które było wcześniej pochodzi bezpośrednio z <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="7910c-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="7910c-134">**Przenoszenie typu z jednego zestawu do innego ✔️**</span><span class="sxs-lookup"><span data-stu-id="7910c-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="7910c-135">Należy pamiętać, że *stare* zestawu musi być oznaczony przez <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> wskazującego na nowego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7910c-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="7910c-136">**✔️ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) typ `readonly struct` typu**</span><span class="sxs-lookup"><span data-stu-id="7910c-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="7910c-137">Należy pamiętać, że zmiana `readonly struct` typ `struct` typ nie jest dozwolony.</span><span class="sxs-lookup"><span data-stu-id="7910c-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="7910c-138">**✔️ Dodawanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) — słowo kluczowe do typu, gdy istnieją nie *dostępny* konstruktory (publiczny lub chroniony)**</span><span class="sxs-lookup"><span data-stu-id="7910c-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="7910c-139">**Rozwijanie widoczność typu ✔️**</span><span class="sxs-lookup"><span data-stu-id="7910c-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="7910c-140">**❌ Zmienianie przestrzeni nazw lub nazwa typu**</span><span class="sxs-lookup"><span data-stu-id="7910c-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="7910c-141">**❌ Zmienianie nazw lub usuwanie typów publicznych**</span><span class="sxs-lookup"><span data-stu-id="7910c-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="7910c-142">Spowoduje to podzielenie cały kod, który używa typu usunięty lub zmieniono jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="7910c-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="7910c-143">**❌ Zmiana podstawowym typem wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="7910c-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="7910c-144">Jest to czasu kompilacji i zachowania istotnej zmiany, a także binarne istotną zmianę, który może zgłaszać błędny argumentów atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7910c-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="7910c-145">**❌ pieczętowania typ, który był wcześniej otwarty**</span><span class="sxs-lookup"><span data-stu-id="7910c-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="7910c-146">**Dodawanie interfejsu do zestawu podstawowych typów interfejsu ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="7910c-147">Jeśli interfejs implementuje interfejs, który ją wcześniej nie implementuje interfejsu, wszystkie typy, które są implementowane oryginalną wersję interfejsu są uszkodzone.</span><span class="sxs-lookup"><span data-stu-id="7910c-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="7910c-148">**Usuwanie klasy z zestawu klas podstawowych lub interfejs z zestawu implementowane interfejsy ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="7910c-149">Istnieje jeden wyjątek reguły do usunięcia interfejsu: można dodać implementacji interfejsu, która wynika z usuniętych interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7910c-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="7910c-150">Na przykład, możesz usunąć <xref:System.IDisposable> Jeśli typ lub interfejs implementuje teraz <xref:System.ComponentModel.IComponent>, który implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="7910c-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="7910c-151">**❌ Zmiana `readonly struct` typ [struktury](../../csharp/language-reference/keywords/struct.md) typu**</span><span class="sxs-lookup"><span data-stu-id="7910c-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="7910c-152">Należy pamiętać, że zmiana `struct` typ `readonly struct` typ jest dozwolony.</span><span class="sxs-lookup"><span data-stu-id="7910c-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="7910c-153">**❌ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) typ `ref struct` typu i na odwrót**</span><span class="sxs-lookup"><span data-stu-id="7910c-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="7910c-154">**Zmniejszanie widoczności typu ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="7910c-155">Jednakże zwiększając widoczność obramowania typem jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="7910c-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="7910c-156">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7910c-156">Members</span></span>

- <span data-ttu-id="7910c-157">**Rozwijanie widoczność elementu członkowskiego, który nie jest ✔️ [wirtualny](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7910c-158">**✔️ Dodawanie abstrakcyjną składową do typu publicznego, który nie ma przypisanego *dostępny* konstruktory (publiczny lub chroniony) lub typ [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="7910c-159">Jednak dodanie abstrakcyjną składową do typu, który jest dostępny żaden konstruktor (publiczny lub chroniony), a nie `sealed` jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="7910c-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="7910c-160">**Ograniczanie widoczności ✔️ [chronione](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych konstruktorów (publiczny lub chroniony) lub typ jest [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7910c-161">**✔️ Przenoszenie członka do klasy wyżej w hierarchii niż typ, z którego został usunięty**</span><span class="sxs-lookup"><span data-stu-id="7910c-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="7910c-162">**✔️ Dodanie lub usunięcie zastąpienia**</span><span class="sxs-lookup"><span data-stu-id="7910c-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="7910c-163">Wprowadzenie do zastąpienia może powodować poprzedniego odbiorcy pominąć zastępowania podczas wywoływania [podstawowy](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="7910c-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="7910c-164">**✔️ Dodanie konstruktora do klasy, wraz z domyślnego (bezparametrowego) konstruktora, jeśli klasa miała wcześniej konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="7910c-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="7910c-165">Jednak dodanie konstruktora do klasy, która miała wcześniej konstruktorów *bez* Dodawanie konstruktora bez parametrów jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="7910c-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="7910c-166">**✔️ Zmiana elementu członkowskiego w [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) do [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="7910c-167">**✔️ Zmiana z `ref readonly` do `ref` zwracają wartość (z wyjątkiem metod wirtualnych lub interfejsów)**</span><span class="sxs-lookup"><span data-stu-id="7910c-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="7910c-168">**✔️ Usunięcie [tylko do odczytu](../../csharp/language-reference/keywords/readonly.md) z polem, chyba że typu statycznego pola jest typem wartości modyfikowalne**</span><span class="sxs-lookup"><span data-stu-id="7910c-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="7910c-169">**✔️ Wywoływania nowe zdarzenie, który nie został wcześniej zdefiniowany**</span><span class="sxs-lookup"><span data-stu-id="7910c-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="7910c-170">**Dodawanie nowego pola wystąpienia typu ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="7910c-171">Ta zmiana wpływa na serializacji.</span><span class="sxs-lookup"><span data-stu-id="7910c-171">This change impacts serialization.</span></span>

- <span data-ttu-id="7910c-172">**❌ Zmienianie nazw lub usuwanie członka publicznego lub parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="7910c-173">Spowoduje to podzielenie cały kod, który używa usunięty lub zmieniono jego nazwę elementu członkowskiego lub parametrów.</span><span class="sxs-lookup"><span data-stu-id="7910c-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="7910c-174">Należy pamiętać, że obejmuje usunięcie lub zmiana nazwy metody pobierającej lub ustawiającej z właściwością, a także zmiana nazwy lub usunięcie elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7910c-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="7910c-175">**Dodawanie członka do interfejsu ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="7910c-176">**❌, zmieniając wartość publiczny członek stałej lub wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="7910c-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="7910c-177">**Zmiana typu właściwości, pola, parametru lub zwracanej wartości ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="7910c-178">**❌ Dodawanie, usuwanie lub zmiana kolejności parametrów**</span><span class="sxs-lookup"><span data-stu-id="7910c-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="7910c-179">**❌ Dodawanie lub usuwanie [w](../../csharp/language-reference/keywords/in.md), [się](../../csharp/language-reference/keywords/out.md) , lub [ref](../../csharp/language-reference/keywords/ref.md) — słowo kluczowe z parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="7910c-180">**❌ Zmiana nazwy parametru (w tym zmienianie jej wielkości liter)**</span><span class="sxs-lookup"><span data-stu-id="7910c-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="7910c-181">Jest uznawane za istotne dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="7910c-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="7910c-182">Przerywa z późnym wiązaniem scenariuszy, takich jak funkcji późne powiązania w języku Visual Basic i [dynamiczne](../../csharp/language-reference/keywords/dynamic.md) w C#.</span><span class="sxs-lookup"><span data-stu-id="7910c-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/keywords/dynamic.md) in C#.</span></span>
  
  - <span data-ttu-id="7910c-183">Przerywa [źródła zgodności](categories.md#source-compatibility) kiedy używać deweloperzy [argumenty nazwane](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="7910c-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="7910c-184">**❌ Zmiana z `ref` wartości zwracanej, aby `ref readonly` zwracają wartość**</span><span class="sxs-lookup"><span data-stu-id="7910c-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="7910c-185">**❌️ Zmiana z `ref readonly` do `ref` zwracają wartość metody wirtualnej lub interfejsu**</span><span class="sxs-lookup"><span data-stu-id="7910c-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="7910c-186">**❌ Dodawanie lub usuwanie [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) od elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="7910c-187">**❌ Usunięcie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe od elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="7910c-188">Chociaż często nie jest to istotna zmiana ponieważ C# kompilatora zwykle do emitowania [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) instrukcje języka pośredniego (IL), aby wywołać metody niewirtualnej (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie ), to zachowanie nie jest invariable z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="7910c-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="7910c-189">C#to nie tylko języka współpracującego .NET.</span><span class="sxs-lookup"><span data-stu-id="7910c-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="7910c-190">C# Kompilator próbuje coraz bardziej zoptymalizować `callvirt` na normalne wywołanie, zawsze wtedy, gdy niewirtualną metodę docelową i prawdopodobnie nie jest null (np. metody udostępnianej [?. operatora propagowania wartości null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="7910c-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="7910c-191">Wprowadzanie metody wirtualnej oznacza, że kod konsumenta często pojawiłyby-niemal jej wywołanie.</span><span class="sxs-lookup"><span data-stu-id="7910c-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="7910c-192">**❌ Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe do elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="7910c-193">**❌ Wprowadzania wirtualny element członkowski jest abstrakcyjna**</span><span class="sxs-lookup"><span data-stu-id="7910c-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="7910c-194">A [wirtualna elementu członkowskiego](../../csharp/language-reference/keywords/virtual.md) dostarcza implementację metody, która *może być* zastąpiona przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="7910c-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="7910c-195">[Abstrakcyjną składową](../../csharp/language-reference/keywords/abstract.md) zapewnia żadnej implementacji i *musi być* przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="7910c-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="7910c-196">**❌ Dodawanie abstrakcyjną składową do typu publicznego, który ma dostępnych konstruktorów (publiczny lub chroniony) i który nie jest [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="7910c-197">**❌ Dodawanie lub usuwanie [statyczne](../../csharp/language-reference/keywords/static.md) — słowo kluczowe od elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="7910c-198">**Dodanie przeciążenia wyklucza istniejących przeciążenia, która definiuje zachowanie różnych ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="7910c-199">Spowoduje to podzielenie istniejących klientów, które były powiązane z poprzednim przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="7910c-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="7910c-200">Na przykład, jeśli klasę utworzono według jednej wersji metody, która akceptuje <xref:System.UInt32>, istniejących klientów pomyślnie powiąże tego przeciążenia przy przekazywaniu <xref:System.Int32> wartość.</span><span class="sxs-lookup"><span data-stu-id="7910c-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="7910c-201">Jednak jeśli dodasz przeciążenia akceptujący <xref:System.Int32>, podczas ponownej kompilacji lub korzystanie z późnym wiązaniem, kompilator teraz wiąże się z nowym przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="7910c-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="7910c-202">Jeśli powoduje różne zachowanie, to istotnej zmiany.</span><span class="sxs-lookup"><span data-stu-id="7910c-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="7910c-203">**❌ Dodanie konstruktora do klasy, która miała wcześniej żaden konstruktor bez dodawania konstruktora bez parametrów**</span><span class="sxs-lookup"><span data-stu-id="7910c-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="7910c-204">**❌️ Dodawanie [tylko do odczytu](../../csharp/language-reference/keywords/readonly.md) do pola**</span><span class="sxs-lookup"><span data-stu-id="7910c-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="7910c-205">**❌ Zmniejszanie widoczności elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="7910c-206">Obejmuje to zmniejszenie widoczność [chronione](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy istnieją *dostępny* konstruktory (publiczny lub chroniony) i typ jest *nie* [ zapieczętowane](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="7910c-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="7910c-207">Jeśli nie jest to możliwe, zmniejszając widoczność chroniony element członkowski jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="7910c-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="7910c-208">Pamiętaj, że zwiększając widoczność elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="7910c-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="7910c-209">**❌ Zmianę typu składowej**</span><span class="sxs-lookup"><span data-stu-id="7910c-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="7910c-210">Nie można zmodyfikować wartość zwracaną metody lub typu pola lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="7910c-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="7910c-211">Na przykład, podpis metody, która zwraca <xref:System.Object> nie można zmienić, aby zwrócić <xref:System.String>, lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="7910c-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="7910c-212">**❌ Dodanie pola do struktury, która miała wcześniej bez stanu**</span><span class="sxs-lookup"><span data-stu-id="7910c-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="7910c-213">Asercja określonego przydziału reguły umożliwia niezainicjowane zmienne tak długo, jak typ zmiennej jest strukturą bezstanowe.</span><span class="sxs-lookup"><span data-stu-id="7910c-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="7910c-214">Jeśli struktura jest stanowa, kod może wystąpić niezainicjowanych danych.</span><span class="sxs-lookup"><span data-stu-id="7910c-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="7910c-215">To plik binarny zmiana powodująca niezgodność oraz potencjalnie źródłowej, które są istotne.</span><span class="sxs-lookup"><span data-stu-id="7910c-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="7910c-216">**Wyzwalanie istniejące zdarzenie, gdy nigdy nie zostało wywołane przed ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="7910c-217">Zmiany zachowania</span><span class="sxs-lookup"><span data-stu-id="7910c-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="7910c-218">Zestawy</span><span class="sxs-lookup"><span data-stu-id="7910c-218">Assemblies</span></span>

- <span data-ttu-id="7910c-219">**✔️ Tworzenie przenośnej zestawu podczas tych samych platformach są nadal obsługiwane.**</span><span class="sxs-lookup"><span data-stu-id="7910c-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="7910c-220">**Zmienianie nazwy zestawu ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="7910c-221">**Zmiana klucza publicznego zestawu ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="7910c-222">Właściwości, pola, parametrów i zwracanych wartości</span><span class="sxs-lookup"><span data-stu-id="7910c-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="7910c-223">**✔️ Zmiana wartości właściwości, pola, wartość zwracana lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr typu bardziej pochodnego**</span><span class="sxs-lookup"><span data-stu-id="7910c-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="7910c-224">Na przykład metodę, która zwraca typ <xref:System.Object> może zwrócić <xref:System.String> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7910c-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="7910c-225">(Jednak sygnatury metody nie można zmienić).</span><span class="sxs-lookup"><span data-stu-id="7910c-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="7910c-226">**Zwiększenie zakresu ✔️ akceptowane wartości dla właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="7910c-227">Pamiętaj, że podczas zakres wartości, które mogą być przekazywane do metody lub są zwracane przez element członkowski można rozwinąć, nie typem parametru lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7910c-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="7910c-228">Na przykład, gdy wartości przekazywane do metody, można zwiększyć z 0 124 0-255, typ parametru nie można zmienić z <xref:System.Byte> do <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="7910c-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="7910c-229">**Zwiększenie zakresu ❌ akceptowane wartości dla właściwości lub parametru, jeśli element jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="7910c-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="7910c-230">Ta zmiana spowoduje przerwanie istniejących zgodnym z przesłoniętą elementy członkowskie, których nie będzie działać prawidłowo dla rozszerzonego zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="7910c-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="7910c-231">**❌ Zmniejszenie zakresu akceptowanych wartości dla właściwości lub parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="7910c-232">**Zwiększenie zakresu ❌ zwracane wartości dla właściwości, pola, wartość zwracana lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="7910c-233">**❌ Zmiana zwracane wartości dla właściwości, pola, wartość zwracana przez metodę, lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="7910c-234">**Zmiana wartości domyślnej właściwości, pola lub parametr ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="7910c-235">**Zmiana dokładność liczbowa wartość zwrotna ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="7910c-236">**Zmiana ❓ A analizowania danych wejściowych i zgłaszanie nowych wyjątków (nawet, jeśli zachowanie analizowania, nie jest określony w dokumentacji**</span><span class="sxs-lookup"><span data-stu-id="7910c-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="7910c-237">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="7910c-237">Exceptions</span></span>

- <span data-ttu-id="7910c-238">**Zgłaszanie wyjątku typu bardziej pochodnego niż istniejący wyjątek ✔️**</span><span class="sxs-lookup"><span data-stu-id="7910c-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="7910c-239">Ponieważ nowy wyjątek jest podklasą istniejących wyjątek, poprzedniego kodu obsługi wyjątków w dalszym ciągu obsłużyć wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7910c-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="7910c-240">Na przykład w programie .NET Framework 4, metod tworzenia i pobierania kultury rozpoczął się zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException> Jeśli nie można odnaleźć kultury.</span><span class="sxs-lookup"><span data-stu-id="7910c-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="7910c-241">Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od klasy <xref:System.ArgumentException>, jest to dopuszczalne zmiany.</span><span class="sxs-lookup"><span data-stu-id="7910c-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="7910c-242">**Zgłaszanie bardziej konkretny wyjątek niż ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="7910c-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="7910c-243">**✔️ zostanie zgłoszony wyjątek, który jest uważany za nieodwracalny**</span><span class="sxs-lookup"><span data-stu-id="7910c-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="7910c-244">Nieodwracalny wyjątki nie powinny być przechwytywane, ale zamiast tego powinno zostać obsłużone przez wysokiego poziomu obsługi catch-all.</span><span class="sxs-lookup"><span data-stu-id="7910c-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="7910c-245">W związku z tym użytkownicy nie powinny mieć kod, który przechwytuje tych jawnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7910c-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="7910c-246">Nieodwracalny wyjątki są:</span><span class="sxs-lookup"><span data-stu-id="7910c-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="7910c-247">**✔️ Zgłaszanie nowy wyjątek nową ścieżkę kodu**</span><span class="sxs-lookup"><span data-stu-id="7910c-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="7910c-248">Wyjątek musi dotyczyć tylko nową ścieżkę kodu które jest wykonywane przy użyciu nowych wartości parametru lub stan i nie można wykonać przez istniejący kod przeznaczonego poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="7910c-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="7910c-249">**Usuwanie wyjątek, aby umożliwić bardziej niezawodne działanie lub udostępnione nowe scenariusze ✔️**</span><span class="sxs-lookup"><span data-stu-id="7910c-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="7910c-250">Na przykład `Divide` metodę, która wcześniej tylko obsługiwane wartości dodatnich i zgłosił <xref:System.ArgumentOutOfRangeException> można zmienić do obsługi wartości dodatnie i ujemne bez zgłoszenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7910c-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="7910c-251">**Zmiana tekstu komunikatu o błędzie ✔️**</span><span class="sxs-lookup"><span data-stu-id="7910c-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="7910c-252">Deweloperzy nie należy polegać na tekst komunikaty o błędach, które zmieniają się również na podstawie kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7910c-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="7910c-253">**❌ w innym przypadku nie jest wymieniona powyżej zostanie zgłoszony wyjątek**</span><span class="sxs-lookup"><span data-stu-id="7910c-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="7910c-254">**Usuwanie wyjątek w innym przypadku niewymienionego powyżej ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="7910c-255">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7910c-255">Attributes</span></span>

- <span data-ttu-id="7910c-256">**✔️, zmieniając wartość atrybutu, który jest *nie* możliwość obserwowania**</span><span class="sxs-lookup"><span data-stu-id="7910c-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="7910c-257">**Zmiana wartości atrybutu ❌, *jest* możliwość obserwowania**</span><span class="sxs-lookup"><span data-stu-id="7910c-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="7910c-258">**Usuwanie atrybutu ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="7910c-259">W większości przypadków, usunięcie atrybutu (takie jak <xref:System.NonSerializedAttribute>) jest zmianą przerywającą.</span><span class="sxs-lookup"><span data-stu-id="7910c-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="7910c-260">Obsługa różnych platform</span><span class="sxs-lookup"><span data-stu-id="7910c-260">Platform support</span></span>

- <span data-ttu-id="7910c-261">**✔️ Obsługi operacji na platformie, która wcześniej nie jest obsługiwana**</span><span class="sxs-lookup"><span data-stu-id="7910c-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="7910c-262">**❌ Nie obsługi lub teraz wymagających określonego dodatku do operacji, która wcześniej była obsługiwana na platformie**</span><span class="sxs-lookup"><span data-stu-id="7910c-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="7910c-263">Wewnętrznej implementacji zmian</span><span class="sxs-lookup"><span data-stu-id="7910c-263">Internal implementation changes</span></span>

- <span data-ttu-id="7910c-264">**Zmienianie obszaru powierzchni wewnętrzny typ ❓**</span><span class="sxs-lookup"><span data-stu-id="7910c-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="7910c-265">Takie zmiany są ogólnie dozwolone, mimo że dzielą się one prywatnej odbicia.</span><span class="sxs-lookup"><span data-stu-id="7910c-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="7910c-266">W niektórych przypadkach, w którym popularnych bibliotek innych firm lub dużej liczby deweloperów zależą od wewnętrznych interfejsach API, takie zmiany może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="7910c-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="7910c-267">**❓ Zmianę wewnętrznej implementacji elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="7910c-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="7910c-268">Te zmiany są ogólnie dozwolone, mimo że dzielą się one prywatnej odbicia.</span><span class="sxs-lookup"><span data-stu-id="7910c-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="7910c-269">W niektórych przypadkach, gdy kod klienta często zależy od prywatnych odbicia lub gdzie zmiany wprowadzono wystąpienie niezamierzonych skutków ubocznych, te zmiany może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="7910c-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="7910c-270">**✔️ Poprawę wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="7910c-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="7910c-271">Możliwość modyfikowania wydajność operacji jest niezbędne, ale takie zmiany może przerwać kodu, która opiera się na bieżącej szybkości operacji.</span><span class="sxs-lookup"><span data-stu-id="7910c-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="7910c-272">Jest to szczególnie istotne, kodu, który jest zależny od czasu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7910c-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="7910c-273">Należy pamiętać, że zmiana wydajności nie powinna mieć żadnego wpływu na inne zachowanie interfejsu API w danym; w przeciwnym razie zostaną istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="7910c-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="7910c-274">**✔️ Pośrednio (i często niekorzystnie) Zmiana wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="7910c-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="7910c-275">Jeśli w danym zmian nie jest traktowane jako podziału innego powodu, jest to dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="7910c-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="7910c-276">Często potrzeba akcje do wykonania, która może zawierać dodatkowe operacje lub dodaje nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="7910c-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="7910c-277">To prawie zawsze mieć wpływ na wydajność, ale może być niezbędny do uzyskania interfejsu API w funkcji pytania, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="7910c-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="7910c-278">**❌ Zmiana synchronicznego interfejsu API do asynchronicznego (i na odwrót)**</span><span class="sxs-lookup"><span data-stu-id="7910c-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="7910c-279">Zmiany w kodzie</span><span class="sxs-lookup"><span data-stu-id="7910c-279">Code changes</span></span>

- <span data-ttu-id="7910c-280">**✔️ Dodawanie [params](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="7910c-281">**❌ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) do [klasy](../../csharp/language-reference/keywords/class.md) i na odwrót**</span><span class="sxs-lookup"><span data-stu-id="7910c-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="7910c-282">**❌ Dodawanie [zaznaczone](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego blok kodu**</span><span class="sxs-lookup"><span data-stu-id="7910c-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="7910c-283">Ta zmiana może spowodować kod, który wcześniej wykonywanego zgłosić <xref:System.OverflowException> i jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="7910c-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="7910c-284">**❌ Usunięcie [params](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="7910c-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="7910c-285">**Zmiana kolejności, w której zdarzenia są uruchamiane ❌**</span><span class="sxs-lookup"><span data-stu-id="7910c-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="7910c-286">Deweloperzy mogą spodziewać zdarzenia w tej samej kolejności, a kod dewelopera zależy często kolejność, w której zdarzenia są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="7910c-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="7910c-287">**❌ Usuwanie wywoływanie zdarzeń w danej akcji**</span><span class="sxs-lookup"><span data-stu-id="7910c-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="7910c-288">**❌ Zmiana liczby danego zdarzenia są wywoływane.**</span><span class="sxs-lookup"><span data-stu-id="7910c-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="7910c-289">**❌ Dodawanie <xref:System.FlagsAttribute> na typ wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="7910c-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
