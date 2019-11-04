---
title: Oszacowanie istotnych zmian — .NET Core
description: Dowiedz się więcej na temat sposobu, w jaki platforma .NET Core próbuje zachować zgodność dla deweloperów w różnych wersjach programu .NET.
ms.date: 06/10/2019
ms.openlocfilehash: a4a1b5c4e81cec783248c6110b0af9844eb3f4af
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416674"
---
# <a name="evaluate-breaking-changes-in-net-core"></a><span data-ttu-id="3873b-103">Oszacowanie istotnych zmian w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="3873b-103">Evaluate breaking changes in .NET Core</span></span>

<span data-ttu-id="3873b-104">W całej historii środowisko .NET podjęło próbę utrzymania wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3873b-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="3873b-105">Jest to nadal prawdziwe dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3873b-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="3873b-106">Mimo że platforma .NET Core może być traktowana jako nowa technologia, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość rozbieżności programu .NET Core od .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3873b-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="3873b-107">Duża liczba deweloperów pierwotnie opracowała lub kontynuowała opracowywanie .NET Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3873b-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="3873b-108">Oczekują one spójnego zachowania w implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3873b-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="3873b-109">.NET Standard projekty biblioteki umożliwiają deweloperom tworzenie bibliotek przeznaczonych dla wspólnych interfejsów API udostępnionych przez platformę .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3873b-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="3873b-110">Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie z tą samą biblioteką używaną w aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3873b-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="3873b-111">Wraz ze zgodnością w ramach implementacji platformy .NET deweloperzy oczekują wysokiego poziomu zgodności między wersjami programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3873b-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="3873b-112">W szczególności kod zapisany dla starszej wersji programu .NET Core powinien działać bezproblemowo na nowszej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3873b-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="3873b-113">W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znajdujące się w nowo wydanej wersji platformy .NET Core powinny również być zgodne z wersjami wstępnymi, w których zostały wprowadzone te interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="3873b-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="3873b-114">W tym artykule przedstawiono kategorie zmian zgodności (lub istotne zmiany) oraz sposób, w jaki zespół .NET oceni zmiany w każdej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="3873b-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="3873b-115">Zrozumienie, w jaki sposób zespół .NET poddaje potencjalne istotne zmiany, jest szczególnie przydatny dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [/corefx](https://github.com/dotnet/corefx) , które modyfikują zachowanie istniejących interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="3873b-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who are opening pull requests in the [dotnet/corefx](https://github.com/dotnet/corefx) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="3873b-116">Aby zapoznać się z definicją kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi wersjami, zobacz artykuł dotyczący [zmiany kategorii](categories.md).</span><span class="sxs-lookup"><span data-stu-id="3873b-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="3873b-117">W poniższych sekcjach opisano kategorie zmian wprowadzonych w interfejsach API programu .NET Core i ich wpływ na zgodność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3873b-117">The following sections describes the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="3873b-118">Ikona ✔️ wskazuje, że określony rodzaj zmiany jest dozwolony, ❌ wskazuje, że jest niedozwolone, a ❓ wskazuje zmianę, która może lub nie jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="3873b-118">The ✔️ icon indicates that a particular kind of change is allowed, ❌ indicates that it is disallowed, and  ❓ indicates a change that may or may not be allowed.</span></span> <span data-ttu-id="3873b-119">Zmiany w tej ostatniej kategorii wymagają orzeczenia i oceny, jak przewidywalne, oczywiste i spójne poprzednie zachowanie było.</span><span class="sxs-lookup"><span data-stu-id="3873b-119">Changes in this last category require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was.</span></span>

> [!NOTE]
> <span data-ttu-id="3873b-120">Oprócz obsługi programu jako wskazówki dotyczącej oceny zmian w bibliotekach .NET Core, deweloperzy biblioteki mogą również używać tych kryteriów do oceny zmian w bibliotekach przeznaczonych dla wielu implementacji i wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3873b-120">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="3873b-121">Modyfikacje kontraktu publicznego</span><span class="sxs-lookup"><span data-stu-id="3873b-121">Modifications to the public contract</span></span>

<span data-ttu-id="3873b-122">Zmiany w tej kategorii *modyfikują* publiczną powierzchnię typu.</span><span class="sxs-lookup"><span data-stu-id="3873b-122">Changes in this category *modify* the public surface area of a type.</span></span> <span data-ttu-id="3873b-123">Większość zmian w tej kategorii jest niedozwolona, ponieważ naruszają *zgodność z poprzednimi* wersjami (zdolność aplikacji, która została opracowana przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="3873b-123">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="3873b-124">Types</span><span class="sxs-lookup"><span data-stu-id="3873b-124">Types</span></span>

- <span data-ttu-id="3873b-125">**✔️ usuwania implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**</span><span class="sxs-lookup"><span data-stu-id="3873b-125">**✔️ Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="3873b-126">**❓ Dodawanie nowej implementacji interfejsu do typu**</span><span class="sxs-lookup"><span data-stu-id="3873b-126">**❓ Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="3873b-127">Jest to akceptowalna zmiana, ponieważ nie ma negatywnego wpływu na istniejących klientów.</span><span class="sxs-lookup"><span data-stu-id="3873b-127">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="3873b-128">Wszelkie zmiany w typie muszą działać w granicach akceptowalnych zmian zdefiniowanych w tym miejscu dla nowej implementacji, która pozostanie akceptowalna.</span><span class="sxs-lookup"><span data-stu-id="3873b-128">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="3873b-129">Należy zachować szczególną ostrożność przy dodawaniu interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatorów do generowania kodu lub danych, których nie można użyć na poziomie niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3873b-129">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="3873b-130">Przykładem jest interfejs <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="3873b-130">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="3873b-131">**❓ Wprowadzenie nowej klasy bazowej**</span><span class="sxs-lookup"><span data-stu-id="3873b-131">**❓ Introducing a new base class**</span></span>

  <span data-ttu-id="3873b-132">Typ może być wprowadzany do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmiany semantyki lub zachowania istniejących typów.</span><span class="sxs-lookup"><span data-stu-id="3873b-132">A type can be introduced into an hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="3873b-133">Na przykład w .NET Framework 2,0, Klasa <xref:System.Data.Common.DbConnection> stała się nową klasą bazową dla <xref:System.Data.SqlClient.SqlConnection>, która wcześniej była bezpośrednio pochodną <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="3873b-133">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="3873b-134">**✔️ przeniesienie typu z jednego zestawu do innego**</span><span class="sxs-lookup"><span data-stu-id="3873b-134">**✔️ Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="3873b-135">Należy zauważyć, że *stary* zestaw musi być oznaczony <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, który wskazuje na nowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="3873b-135">Note that the *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="3873b-136">**✔️ zmienić typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="3873b-136">**✔️ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="3873b-137">Należy zauważyć, że zmiana typu `readonly struct` na typ `struct` jest niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="3873b-137">Note that changing a `readonly struct` type to a `struct` type is not allowed.</span></span>
  
- <span data-ttu-id="3873b-138">**✔️ dodawania [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu, gdy nie ma *dostępnych* (publicznych lub chronionych) konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="3873b-138">**✔️ Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="3873b-139">**✔️ Rozszerzanie widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="3873b-139">**✔️ Expanding the visibility of a type**</span></span>

- <span data-ttu-id="3873b-140">**❌ zmienić przestrzeni nazw lub nazwy typu**</span><span class="sxs-lookup"><span data-stu-id="3873b-140">**❌ Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="3873b-141">**❌ Zmienianie nazwy lub usuwanie typu publicznego**</span><span class="sxs-lookup"><span data-stu-id="3873b-141">**❌ Renaming or removing a public type**</span></span>

   <span data-ttu-id="3873b-142">Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.</span><span class="sxs-lookup"><span data-stu-id="3873b-142">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="3873b-143">**❌ Zmienianie typu podstawowego wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3873b-143">**❌ Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="3873b-144">Jest to niezależna od czasu kompilowania i zachowania zmiana, a także zmiana podziału binarnego, która może sprawiać, że argumenty atrybutów nie są przewidziane do przeanalizowania.</span><span class="sxs-lookup"><span data-stu-id="3873b-144">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="3873b-145">**❌ opieczętowanie typu, który był wcześniej niezapieczętowany**</span><span class="sxs-lookup"><span data-stu-id="3873b-145">**❌ Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="3873b-146">**❌ dodawania interfejsu do zestawu typów podstawowych interfejsu**</span><span class="sxs-lookup"><span data-stu-id="3873b-146">**❌ Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="3873b-147">Jeśli interfejs implementuje interfejs, który wcześniej nie został zaimplementowany, wszystkie typy, które implementują oryginalną wersję interfejsu, są uszkodzone.</span><span class="sxs-lookup"><span data-stu-id="3873b-147">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="3873b-148">**❓ Usunięcie klasy z zestawu klas bazowych lub interfejsu z zestawu zaimplementowanych interfejsów**</span><span class="sxs-lookup"><span data-stu-id="3873b-148">**❓ Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="3873b-149">Istnieje jeden wyjątek dla reguły usuwania interfejsu: można dodać implementację interfejsu, która pochodzi od usuniętego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3873b-149">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="3873b-150">Na przykład można usunąć <xref:System.IDisposable>, jeśli typ lub interfejs implementuje teraz <xref:System.ComponentModel.IComponent>, który implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="3873b-150">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="3873b-151">**❌ zmienić typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-151">**❌ Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="3873b-152">Należy zauważyć, że zmiana typu `struct` na typ `readonly struct` jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="3873b-152">Note that the change of a `struct` type to a `readonly struct` type is allowed.</span></span>

- <span data-ttu-id="3873b-153">**❌ zmienić typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` i odwrotnie**</span><span class="sxs-lookup"><span data-stu-id="3873b-153">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="3873b-154">**❌ zmniejszania widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="3873b-154">**❌ Reducing the visibility of a type**</span></span>

   <span data-ttu-id="3873b-155">Jednak zwiększenie widoczności typu jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-155">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="3873b-156">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3873b-156">Members</span></span>

- <span data-ttu-id="3873b-157">**✔️ Rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-157">**✔️ Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3873b-158">**✔️ dodawania abstrakcyjnej składowej do typu publicznego, który ma *niedostępne* (publiczne lub chronione) konstruktory lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-158">**✔️ Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="3873b-159">Jednak dodanie abstrakcyjnej składowej do typu, który ma dostępne (publiczne lub chronione) konstruktorów, i nie jest `sealed` jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-159">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="3873b-160">**✔️ Ograniczanie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-160">**✔️ Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3873b-161">**✔️ przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**</span><span class="sxs-lookup"><span data-stu-id="3873b-161">**✔️ Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="3873b-162">**✔️ Dodawanie lub usuwanie przesłonięcia**</span><span class="sxs-lookup"><span data-stu-id="3873b-162">**✔️ Adding or removing an override**</span></span>

  <span data-ttu-id="3873b-163">Należy pamiętać, że wprowadzenie przesłonięcia może spowodować, że poprzedni odbiorcy pominięcia przesłonięcia podczas wywoływania [podstawy](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="3873b-163">Note that introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="3873b-164">**✔️ dodać konstruktora do klasy wraz z domyślnym konstruktorem (bez parametrów), jeśli Klasa nie miała wcześniej konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="3873b-164">**✔️ Adding a constructor to a class, along with a default (parameterless) constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="3873b-165">Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrowego, nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-165">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="3873b-166">**✔️ zmienić elementu członkowskiego z [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) na [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-166">**✔️ Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="3873b-167">**✔️ zmienić z `ref readonly` na `ref` wartość zwrotną (z wyjątkiem metod wirtualnych lub interfejsów)**</span><span class="sxs-lookup"><span data-stu-id="3873b-167">**✔️ Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="3873b-168">**✔️ Usuwanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest modyfikowalnym typem wartości**</span><span class="sxs-lookup"><span data-stu-id="3873b-168">**✔️ Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="3873b-169">**✔️ Wywoływanie nowego zdarzenia, które nie zostało wcześniej zdefiniowane**</span><span class="sxs-lookup"><span data-stu-id="3873b-169">**✔️ Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="3873b-170">**❓ Dodać nowego pola wystąpienia do typu**</span><span class="sxs-lookup"><span data-stu-id="3873b-170">**❓ Adding a new instance field to a type**</span></span>

   <span data-ttu-id="3873b-171">Ta zmiana wpływa na serializację.</span><span class="sxs-lookup"><span data-stu-id="3873b-171">This change impacts serialization.</span></span>

- <span data-ttu-id="3873b-172">**❌ Zmienianie nazwy lub usuwanie publicznego elementu członkowskiego lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-172">**❌ Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="3873b-173">Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego elementu członkowskiego lub parametru.</span><span class="sxs-lookup"><span data-stu-id="3873b-173">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="3873b-174">Należy zauważyć, że obejmuje to usunięcie lub zmianę nazwy metody pobierającej lub setter z właściwości, a także zmianę nazwy lub usunięcie elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3873b-174">Note that this includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="3873b-175">**❌ Dodawanie elementu członkowskiego do interfejsu**</span><span class="sxs-lookup"><span data-stu-id="3873b-175">**❌ Adding a member to an interface**</span></span>

- <span data-ttu-id="3873b-176">**❌ zmienić wartości stałej publicznej lub składowej wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3873b-176">**❌ Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="3873b-177">**❌ zmienić typu właściwości, pola, parametru lub wartości zwracanej**</span><span class="sxs-lookup"><span data-stu-id="3873b-177">**❌ Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="3873b-178">**❌ dodawania, usuwania lub zmiany kolejności parametrów**</span><span class="sxs-lookup"><span data-stu-id="3873b-178">**❌ Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="3873b-179">**❌ Dodawanie lub usuwanie słowa kluczowego [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-179">**❌ Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="3873b-180">**❌ zmianę nazwy parametru (w tym zmiana jego wielkości liter)**</span><span class="sxs-lookup"><span data-stu-id="3873b-180">**❌ Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="3873b-181">Jest to uważane za rozdzielenie z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="3873b-181">This is considered breaking for two reasons:</span></span>
  
  - <span data-ttu-id="3873b-182">Dzieli scenariusze z późnym wiązaniem, takie jak funkcja późnego wiązania w Visual Basic C#i [dynamiczna](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) w.</span><span class="sxs-lookup"><span data-stu-id="3873b-182">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>
  
  - <span data-ttu-id="3873b-183">Jest ona podzielona na [zgodność źródłową](categories.md#source-compatibility) , gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="3873b-183">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="3873b-184">**❌ zmienić z `ref` wartości zwracanej na `ref readonly` wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3873b-184">**❌ Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="3873b-185">**❌️ zmiany z `ref readonly` na `ref` wartość zwrotną w wirtualnej metodzie lub interfejsie**</span><span class="sxs-lookup"><span data-stu-id="3873b-185">**❌️ Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="3873b-186">**❌ Dodawanie lub usuwanie [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-186">**❌ Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="3873b-187">**❌ usunięcie słowa kluczowego [Virtual](../../csharp/language-reference/keywords/virtual.md) z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-187">**❌ Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="3873b-188">Chociaż często nie jest to istotna zmiana, C# ponieważ kompilator zamierza emitować instrukcje języka pośredniego (IL) elementu [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) do wywoływania metod niewirtualnych (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie jest), to zachowanie nie jest Niezmienna z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="3873b-188">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="3873b-189">C#nie jest jedynym językiem, który jest obiektem docelowym platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3873b-189">C# is not the only language that .NET targets.</span></span>
  
  - <span data-ttu-id="3873b-190">C# Kompilator coraz bardziej próbuje zoptymalizować `callvirt` do normalnego wywołania, gdy metoda docelowa nie jest wirtualna i prawdopodobnie nie ma wartości null (na przykład metodę dostępną za pomocą [operatora propagacji?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="3873b-190">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>
  
  <span data-ttu-id="3873b-191">Zastosowanie metody wirtualnej oznacza, że kod konsumenta często kończy wywoływanie go niepraktycznie.</span><span class="sxs-lookup"><span data-stu-id="3873b-191">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="3873b-192">**❌ dodawania słowa kluczowego [Virtual](../../csharp/language-reference/keywords/virtual.md) do elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-192">**❌ Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="3873b-193">**❌ tworzenia abstrakcyjnej składowej wirtualnego**</span><span class="sxs-lookup"><span data-stu-id="3873b-193">**❌ Making a virtual member abstract**</span></span>

  <span data-ttu-id="3873b-194">[Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zawiera implementację metody, która *może zostać* zastąpiona przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="3873b-194">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="3873b-195">[Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zawiera implementacji i *musi zostać* zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="3873b-195">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="3873b-196">**❌ dodawania abstrakcyjnej składowej do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory, które nie są [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-196">**❌ Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3873b-197">**❌ Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-197">**❌ Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="3873b-198">**❌ dodawania przeciążenia, które wyklucza istniejące Przeciążenie i definiuje inne zachowanie**</span><span class="sxs-lookup"><span data-stu-id="3873b-198">**❌ Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="3873b-199">Spowoduje to przerwanie istniejących klientów, które zostały powiązane z poprzednim przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="3873b-199">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="3873b-200">Na przykład jeśli klasa ma jedną wersję metody, która akceptuje <xref:System.UInt32>, istniejący Klient pomyślnie powiąże się z tym przeciążeniem podczas przekazywania wartości <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="3873b-200">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="3873b-201">Jednakże jeśli dodasz Przeciążenie, które akceptuje <xref:System.Int32>, podczas ponownego kompilowania lub korzystania z późnego wiązania, kompilator teraz tworzy powiązanie z nowym przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="3873b-201">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="3873b-202">W przypadku innych wyników zachowania jest to istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="3873b-202">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="3873b-203">**❌ dodać konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrowego**</span><span class="sxs-lookup"><span data-stu-id="3873b-203">**❌ Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="3873b-204">**❌️ dodawania do pola [tylko do odczytu](../../csharp/language-reference/keywords/readonly.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-204">**❌️ Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="3873b-205">**❌ zmniejszania widoczności elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-205">**❌ Reducing the visibility of a member**</span></span>

   <span data-ttu-id="3873b-206">Obejmuje to zmniejszenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy są *dostępne* (publiczne lub chronione) konstruktory, a typ *nie* jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="3873b-206">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (public or protected) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="3873b-207">Jeśli tak się nie dzieje, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-207">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="3873b-208">Należy zauważyć, że zwiększenie widoczności składowej jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-208">Note that increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="3873b-209">**❌ zmienić typu elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-209">**❌ Changing the type of a member**</span></span>

   <span data-ttu-id="3873b-210">Nie można zmodyfikować wartości zwracanej przez metodę lub typ właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="3873b-210">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="3873b-211">Na przykład sygnatura metody zwracającej <xref:System.Object> nie może zostać zmieniona w celu zwrócenia <xref:System.String>lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="3873b-211">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="3873b-212">**❌ Dodawanie pola do struktury, która wcześniej nie miała stanu**</span><span class="sxs-lookup"><span data-stu-id="3873b-212">**❌ Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="3873b-213">Określone reguły przypisywania umożliwiają użycie niezainicjowanych zmiennych, tak długo, jak typ zmiennej jest strukturą bezstanową.</span><span class="sxs-lookup"><span data-stu-id="3873b-213">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="3873b-214">Jeśli struktura jest stanowa, kod może kończyć się zainicjowanymi danymi.</span><span class="sxs-lookup"><span data-stu-id="3873b-214">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="3873b-215">Może to być zarówno uszkodzenie źródła, jak i uszkodzenie binarne.</span><span class="sxs-lookup"><span data-stu-id="3873b-215">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="3873b-216">**❌ wyzwalanie istniejącego zdarzenia, gdy wcześniej nie zostało ono wyzwolone**</span><span class="sxs-lookup"><span data-stu-id="3873b-216">**❌ Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="3873b-217">Zmiany behawioralne</span><span class="sxs-lookup"><span data-stu-id="3873b-217">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="3873b-218">Zestawy</span><span class="sxs-lookup"><span data-stu-id="3873b-218">Assemblies</span></span>

- <span data-ttu-id="3873b-219">**✔️ tworzenia zestawu przenośnego, gdy te same platformy są nadal obsługiwane**</span><span class="sxs-lookup"><span data-stu-id="3873b-219">**✔️ Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="3873b-220">**❌ zmienić nazwy zestawu**</span><span class="sxs-lookup"><span data-stu-id="3873b-220">**❌ Changing the name of an assembly**</span></span>
- <span data-ttu-id="3873b-221">**❌ zmienić klucza publicznego zestawu**</span><span class="sxs-lookup"><span data-stu-id="3873b-221">**❌ Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="3873b-222">Właściwości, pola, parametry i wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="3873b-222">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="3873b-223">**✔️ zmiany wartości właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na bardziej pochodny typ**</span><span class="sxs-lookup"><span data-stu-id="3873b-223">**✔️ Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="3873b-224">Na przykład Metoda zwracająca typ <xref:System.Object> może zwracać wystąpienie <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3873b-224">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="3873b-225">Nie można jednak zmienić sygnatury metody.)</span><span class="sxs-lookup"><span data-stu-id="3873b-225">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="3873b-226">**✔️ zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-226">**✔️ Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="3873b-227">Należy zauważyć, że podczas gdy zakres wartości, które mogą być przesyłane do metody lub są zwracane przez element członkowski, można rozwinąć, parametr lub typ elementu członkowskiego nie mogą.</span><span class="sxs-lookup"><span data-stu-id="3873b-227">Note that while the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="3873b-228">Na przykład, podczas gdy wartości przesyłane do metody mogą rozszerzać od 0-124 do 0-255, typ parametru nie może ulec zmianie z <xref:System.Byte> na <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="3873b-228">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="3873b-229">**❌ zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-229">**❌ Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="3873b-230">Ta zmiana powoduje przerwanie istniejących przesłoniętych elementów członkowskich, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="3873b-230">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="3873b-231">**❌ zmniejszania zakresu akceptowanych wartości dla właściwości lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-231">**❌ Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="3873b-232">**❌ zwiększyć zakres wartości zwracanych dla właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-232">**❌ Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3873b-233">**❌ zmienić zwracanych wartości dla właściwości, pola, wartości zwracanej metody lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="3873b-233">**❌ Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3873b-234">**❌ zmiany wartości domyślnej właściwości, pola lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-234">**❌ Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="3873b-235">**❌ zmiany dokładności liczbowej zwracanej wartości**</span><span class="sxs-lookup"><span data-stu-id="3873b-235">**❌ Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="3873b-236">**❓ Zmianę podczas analizowania danych wejściowych i zgłaszających nowe wyjątki (nawet jeśli nie określono zachowania analizy w dokumentacji**</span><span class="sxs-lookup"><span data-stu-id="3873b-236">**❓ A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="3873b-237">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3873b-237">Exceptions</span></span>

- <span data-ttu-id="3873b-238">**✔️ Zgłaszanie bardziej pochodnego wyjątku niż istniejący wyjątek**</span><span class="sxs-lookup"><span data-stu-id="3873b-238">**✔️ Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="3873b-239">Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsłużył wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3873b-239">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="3873b-240">Na przykład w .NET Framework 4, metody tworzenia i pobierania kultur zaczęły zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException>, jeśli nie można odnaleźć kultury.</span><span class="sxs-lookup"><span data-stu-id="3873b-240">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="3873b-241">Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od <xref:System.ArgumentException>, jest to akceptowalna zmiana.</span><span class="sxs-lookup"><span data-stu-id="3873b-241">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="3873b-242">**✔️ zgłaszania bardziej szczegółowego wyjątku niż <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="3873b-242">**✔️ Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="3873b-243">**✔️ zgłaszania wyjątku, który jest uznawany za niemożliwy do odzyskania**</span><span class="sxs-lookup"><span data-stu-id="3873b-243">**✔️ Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="3873b-244">Niemożliwy do odzyskania wyjątki nie powinny być przechwytywane, ale powinny być obsługiwane przez obsługę catch-all o wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="3873b-244">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="3873b-245">W związku z tym użytkownicy nie powinny mieć kodu, który przechwytuje te jawne wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3873b-245">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="3873b-246">Nieodwracalne wyjątki są następujące:</span><span class="sxs-lookup"><span data-stu-id="3873b-246">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="3873b-247">**✔️ Zgłaszanie nowego wyjątku w nowej ścieżce kodu**</span><span class="sxs-lookup"><span data-stu-id="3873b-247">**✔️ Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="3873b-248">Wyjątek musi dotyczyć tylko nowej ścieżki kodu, która jest wykonywana przy użyciu nowych wartości parametrów lub stanu, i które nie mogą być wykonywane przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3873b-248">The exception must apply only to a new code-path which is executed with new parameter values or state, and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="3873b-249">**✔️ usunąć wyjątek, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**</span><span class="sxs-lookup"><span data-stu-id="3873b-249">**✔️ Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="3873b-250">Na przykład Metoda `Divide`, która wcześniej obsługiwała tylko wartości dodatnie i wywołała <xref:System.ArgumentOutOfRangeException> w przeciwnym razie można zmienić, aby obsługiwała wartości ujemne i dodatnie bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3873b-250">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="3873b-251">**✔️ zmienić tekstu komunikatu o błędzie**</span><span class="sxs-lookup"><span data-stu-id="3873b-251">**✔️ Changing the text of an error message**</span></span>

  <span data-ttu-id="3873b-252">Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3873b-252">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="3873b-253">**❌ zgłaszanie wyjątku w innym przypadku niewymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="3873b-253">**❌ Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="3873b-254">**❌ usunąć wyjątek w każdym innym przypadku niewymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="3873b-254">**❌ Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="3873b-255">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3873b-255">Attributes</span></span>

- <span data-ttu-id="3873b-256">**✔️ zmienić wartości atrybutu, który *nie* jest zauważalny**</span><span class="sxs-lookup"><span data-stu-id="3873b-256">**✔️ Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="3873b-257">**❌ zmienić wartości atrybutu, który *jest* zauważalny**</span><span class="sxs-lookup"><span data-stu-id="3873b-257">**❌ Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="3873b-258">**❓ Usunąć atrybutu**</span><span class="sxs-lookup"><span data-stu-id="3873b-258">**❓ Removing an attribute**</span></span>

  <span data-ttu-id="3873b-259">W większości przypadków usunięcie atrybutu (takiego jak <xref:System.NonSerializedAttribute>) jest istotną zmianą.</span><span class="sxs-lookup"><span data-stu-id="3873b-259">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="3873b-260">Obsługa platform</span><span class="sxs-lookup"><span data-stu-id="3873b-260">Platform support</span></span>

- <span data-ttu-id="3873b-261">**✔️ Obsługa operacji na platformie, która była wcześniej nieobsługiwana**</span><span class="sxs-lookup"><span data-stu-id="3873b-261">**✔️ Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="3873b-262">**❌ nie obsługiwać lub obecnie wymaganego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**</span><span class="sxs-lookup"><span data-stu-id="3873b-262">**❌ Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="3873b-263">Wewnętrzne zmiany implementacji</span><span class="sxs-lookup"><span data-stu-id="3873b-263">Internal implementation changes</span></span>

- <span data-ttu-id="3873b-264">**❓ Zmienić obszaru powierzchni typu wewnętrznego**</span><span class="sxs-lookup"><span data-stu-id="3873b-264">**❓ Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="3873b-265">Takie zmiany są zwykle dozwolone, chociaż przerywają odbicie prywatne.</span><span class="sxs-lookup"><span data-stu-id="3873b-265">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3873b-266">W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależą od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-266">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="3873b-267">**❓ Zmiana wewnętrznej implementacji elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3873b-267">**❓ Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="3873b-268">Te zmiany są ogólnie dozwolone, chociaż przerywają odbicie prywatne.</span><span class="sxs-lookup"><span data-stu-id="3873b-268">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3873b-269">W niektórych przypadkach, gdzie kod klienta często zależy od odbicia prywatnego lub gdzie zmiana wprowadza niezamierzone efekty uboczne, te zmiany mogą być niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="3873b-269">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="3873b-270">**✔️ poprawy wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="3873b-270">**✔️ Improving the performance of an operation**</span></span>

   <span data-ttu-id="3873b-271">Możliwość modyfikowania wydajności operacji jest istotna, ale takie zmiany mogą spowodować przerwanie kodu, który opiera się na bieżącej szybkości operacji.</span><span class="sxs-lookup"><span data-stu-id="3873b-271">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="3873b-272">Jest to szczególnie prawdziwe w przypadku kodu, który zależy od chronometrażu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="3873b-272">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="3873b-273">Należy zauważyć, że zmiana wydajności nie powinna mieć wpływu na inne zachowanie interfejsu API. w przeciwnym razie zmiana zostanie przerwana.</span><span class="sxs-lookup"><span data-stu-id="3873b-273">Note that the performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="3873b-274">**✔️ pośrednio (i często nieszkodliwe) zmiana wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="3873b-274">**✔️ Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="3873b-275">Jeśli dana zmiana nie zostanie skategoryzowana z innego powodu, jest to dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="3873b-275">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="3873b-276">Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub dodając nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="3873b-276">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="3873b-277">Prawie zawsze ma to wpływ na wydajność, ale może być konieczne, aby interfejs API działał w oczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="3873b-277">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="3873b-278">**❌ zmiany synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**</span><span class="sxs-lookup"><span data-stu-id="3873b-278">**❌ Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="3873b-279">Zmiany kodu</span><span class="sxs-lookup"><span data-stu-id="3873b-279">Code changes</span></span>

- <span data-ttu-id="3873b-280">**✔️ dodawania [parametrów](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-280">**✔️ Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="3873b-281">**❌ zmienić [struktury](../../csharp/language-reference/keywords/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**</span><span class="sxs-lookup"><span data-stu-id="3873b-281">**❌ Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="3873b-282">**❌ dodawania słowa kluczowego [Checked](../../csharp/language-reference/keywords/virtual.md) do bloku kodu**</span><span class="sxs-lookup"><span data-stu-id="3873b-282">**❌ Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="3873b-283">Ta zmiana może spowodować, że kod, który został wcześniej wykonany, aby zgłosić <xref:System.OverflowException> i jest nieakceptowalny.</span><span class="sxs-lookup"><span data-stu-id="3873b-283">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="3873b-284">**❌ usuwanie [parametrów](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="3873b-284">**❌ Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="3873b-285">**❌ zmienić kolejność, w której są uruchamiane zdarzenia**</span><span class="sxs-lookup"><span data-stu-id="3873b-285">**❌ Changing the order in which events are fired**</span></span>

  <span data-ttu-id="3873b-286">Deweloperzy mogą w rozsądny sposób oczekiwać, że wyzwalają zdarzenia w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3873b-286">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="3873b-287">**❌ usunąć podnoszenie poziomu zdarzenia na daną akcję**</span><span class="sxs-lookup"><span data-stu-id="3873b-287">**❌ Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="3873b-288">**❌ zmienić liczbę wywoływanych zdarzeń**</span><span class="sxs-lookup"><span data-stu-id="3873b-288">**❌ Changing the number of times given events are called**</span></span>

- <span data-ttu-id="3873b-289">**❌ Dodawanie <xref:System.FlagsAttribute> do typu wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3873b-289">**❌ Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
