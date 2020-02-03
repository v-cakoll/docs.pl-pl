---
title: Typy istotnych zmian — .NET Core
description: Dowiedz się, jak platforma .NET Core próbuje zachować zgodność dla deweloperów w różnych wersjach programu .NET i jakiego rodzaju zmiana jest traktowana jako istotna zmiana.
ms.date: 06/10/2019
ms.openlocfilehash: 76d04504c4476f0f7517a633cfbf1c0aa9d5797e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738572"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="3e25b-103">Zmiany wpływające na zgodność</span><span class="sxs-lookup"><span data-stu-id="3e25b-103">Changes that affect compatibility</span></span>

<span data-ttu-id="3e25b-104">W całej historii środowisko .NET podjęło próbę utrzymania wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e25b-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="3e25b-105">Jest to nadal prawdziwe dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e25b-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="3e25b-106">Mimo że platforma .NET Core może być traktowana jako nowa technologia, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość rozbieżności programu .NET Core od .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="3e25b-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="3e25b-107">Duża liczba deweloperów pierwotnie opracowała lub kontynuowała opracowywanie .NET Framework aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e25b-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="3e25b-108">Oczekują one spójnego zachowania w implementacjach platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e25b-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="3e25b-109">.NET Standard projekty biblioteki umożliwiają deweloperom tworzenie bibliotek przeznaczonych dla wspólnych interfejsów API udostępnionych przez platformę .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e25b-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="3e25b-110">Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie z tą samą biblioteką używaną w aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e25b-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="3e25b-111">Wraz ze zgodnością w ramach implementacji platformy .NET deweloperzy oczekują wysokiego poziomu zgodności między wersjami programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e25b-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="3e25b-112">W szczególności kod zapisany dla starszej wersji programu .NET Core powinien działać bezproblemowo na nowszej wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e25b-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="3e25b-113">W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znajdujące się w nowo wydanej wersji platformy .NET Core powinny również być zgodne z wersjami wstępnymi, w których zostały wprowadzone te interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="3e25b-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="3e25b-114">W tym artykule przedstawiono kategorie zmian zgodności (lub istotne zmiany) oraz sposób, w jaki zespół .NET oceni zmiany w każdej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="3e25b-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="3e25b-115">Zrozumienie, w jaki sposób zespół .NET zbliża się do możliwych istotnych zmian, jest szczególnie przydatny dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [/środowiska uruchomieniowego](https://github.com/dotnet/runtime) w serwisie w witrynie w serwisie w serwisie w witrynie</span><span class="sxs-lookup"><span data-stu-id="3e25b-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="3e25b-116">Aby zapoznać się z definicją kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi wersjami, zobacz artykuł dotyczący [zmiany kategorii](categories.md).</span><span class="sxs-lookup"><span data-stu-id="3e25b-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="3e25b-117">W poniższych sekcjach opisano kategorie zmian wprowadzonych w interfejsach API programu .NET Core i ich wpływ na zgodność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3e25b-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="3e25b-118">Zmiany są dozwolone ✔️, niedozwolone ❌lub wymagają orzeczenia oraz oceny sposobu, w jaki przewidywalne, oczywiste i spójne poprzednie zachowanie zostało ❓.</span><span class="sxs-lookup"><span data-stu-id="3e25b-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="3e25b-119">Oprócz obsługi programu jako wskazówki dotyczącej oceny zmian w bibliotekach .NET Core, deweloperzy biblioteki mogą również używać tych kryteriów do oceny zmian w bibliotekach przeznaczonych dla wielu implementacji i wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e25b-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="3e25b-120">Modyfikacje kontraktu publicznego</span><span class="sxs-lookup"><span data-stu-id="3e25b-120">Modifications to the public contract</span></span>

<span data-ttu-id="3e25b-121">Zmiany w tej kategorii modyfikują publiczną powierzchnię typu.</span><span class="sxs-lookup"><span data-stu-id="3e25b-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="3e25b-122">Większość zmian w tej kategorii jest niedozwolona, ponieważ naruszają *zgodność z poprzednimi* wersjami (zdolność aplikacji, która została opracowana przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="3e25b-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="3e25b-123">Types</span><span class="sxs-lookup"><span data-stu-id="3e25b-123">Types</span></span>

- <span data-ttu-id="3e25b-124">✔️ **dozwolone: usuwanie implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**</span><span class="sxs-lookup"><span data-stu-id="3e25b-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="3e25b-125">❓ **Wymaga orzeczenia: Dodawanie nowej implementacji interfejsu do typu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="3e25b-126">Jest to akceptowalna zmiana, ponieważ nie ma negatywnego wpływu na istniejących klientów.</span><span class="sxs-lookup"><span data-stu-id="3e25b-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="3e25b-127">Wszelkie zmiany w typie muszą działać w granicach akceptowalnych zmian zdefiniowanych w tym miejscu dla nowej implementacji, która pozostanie akceptowalna.</span><span class="sxs-lookup"><span data-stu-id="3e25b-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="3e25b-128">Należy zachować szczególną ostrożność przy dodawaniu interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatorów do generowania kodu lub danych, których nie można użyć na poziomie niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3e25b-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="3e25b-129">Przykładem jest interfejs <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="3e25b-130">❓ **Wymaga orzeczenia: wprowadzenie nowej klasy bazowej**</span><span class="sxs-lookup"><span data-stu-id="3e25b-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="3e25b-131">Typ może być wprowadzany do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmiany semantyki lub zachowania istniejących typów.</span><span class="sxs-lookup"><span data-stu-id="3e25b-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="3e25b-132">Na przykład w .NET Framework 2,0, Klasa <xref:System.Data.Common.DbConnection> stała się nową klasą bazową dla <xref:System.Data.SqlClient.SqlConnection>, która wcześniej była bezpośrednio pochodną <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="3e25b-133">✔️ **dozwolone: przeniesienie typu z jednego zestawu do innego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="3e25b-134">*Stary* zestaw musi być oznaczony <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, który wskazuje na nowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="3e25b-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="3e25b-135">✔️ **dozwolone: zmiana typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**</span><span class="sxs-lookup"><span data-stu-id="3e25b-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="3e25b-136">Zmiana typu `readonly struct` na typ `struct` jest niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="3e25b-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="3e25b-137">✔️ **dozwolone: dodanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu w przypadku braku *dostępnych* (publicznych lub chronionych) konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="3e25b-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="3e25b-138">✔️ **dozwolone: rozszerzanie widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="3e25b-139">niedozwolone ❌ **: zmiana przestrzeni nazw lub nazwy typu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="3e25b-140">niedozwolone ❌ **: zmiana nazwy lub usuwanie typu publicznego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="3e25b-141">Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.</span><span class="sxs-lookup"><span data-stu-id="3e25b-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="3e25b-142">niedozwolone ❌ **: zmiana podstawowego typu wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="3e25b-143">Jest to niezależna od czasu kompilowania i zachowania zmiana, a także zmiana podziału binarnego, która może sprawiać, że argumenty atrybutów nie są przewidziane do przeanalizowania.</span><span class="sxs-lookup"><span data-stu-id="3e25b-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="3e25b-144">niedozwolone ❌ **: opieczętowanie typu, który był wcześniej niezapieczętowany**</span><span class="sxs-lookup"><span data-stu-id="3e25b-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="3e25b-145">niedozwolone ❌ **: Dodawanie interfejsu do zestawu typów podstawowych interfejsu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="3e25b-146">Jeśli interfejs implementuje interfejs, który wcześniej nie został zaimplementowany, wszystkie typy, które implementują oryginalną wersję interfejsu, są uszkodzone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="3e25b-147">❓ **Wymaga orzeczenia: usunięcie klasy z zestawu klas bazowych lub interfejsu z zestawu zaimplementowanych interfejsów**</span><span class="sxs-lookup"><span data-stu-id="3e25b-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="3e25b-148">Istnieje jeden wyjątek dla reguły usuwania interfejsu: można dodać implementację interfejsu, która pochodzi od usuniętego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="3e25b-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="3e25b-149">Na przykład można usunąć <xref:System.IDisposable>, jeśli typ lub interfejs implementuje teraz <xref:System.ComponentModel.IComponent>, który implementuje <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="3e25b-150">niedozwolone ❌ **: zmiana typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/keywords/struct.md) type**</span></span>

  <span data-ttu-id="3e25b-151">Istnieje jednak możliwość zmiany typu `struct` typu `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="3e25b-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="3e25b-152">niedozwolone ❌ **: zmiana typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` i odwrotnie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="3e25b-153">niedozwolone ❌ **: zmniejszanie widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="3e25b-154">Jednak zwiększenie widoczności typu jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="3e25b-155">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3e25b-155">Members</span></span>

- <span data-ttu-id="3e25b-156">✔️ **dozwolone: rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3e25b-157">✔️ **dozwolone: Dodawanie abstrakcyjnej składowej do typu publicznego, który nie ma *dostępnych* (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="3e25b-158">Jednak dodanie abstrakcyjnej składowej do typu, który ma dostępne (publiczne lub chronione) konstruktorów, i nie jest `sealed` jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="3e25b-159">✔️ **dozwolone: ograniczanie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3e25b-160">✔️ **dozwolone: przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**</span><span class="sxs-lookup"><span data-stu-id="3e25b-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="3e25b-161">✔️ **dozwolone: Dodawanie lub usuwanie przesłonięcia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="3e25b-162">Wprowadzenie przesłonięcia może spowodować, że poprzedni odbiorcy pominięcia przesłonięcia podczas wywoływania [podstawy](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="3e25b-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="3e25b-163">✔️ **dozwolone: Dodawanie konstruktora do klasy wraz z konstruktorem bez parametrów, jeśli Klasa nie miała wcześniej konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="3e25b-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="3e25b-164">Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrowego, nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="3e25b-165">✔️ **dozwolone: zmiana składowej z [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) na [wirtualną](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="3e25b-166">✔️ **dozwolone: zmiana z `ref readonly` na `ref` wartość zwracana (z wyjątkiem metod wirtualnych lub interfejsów)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="3e25b-167">✔️ **dozwolone: usuwanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest modyfikowalnym typem wartości**</span><span class="sxs-lookup"><span data-stu-id="3e25b-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="3e25b-168">✔️ **dozwolone: wywoływanie nowego zdarzenia, które nie zostało wcześniej zdefiniowane**</span><span class="sxs-lookup"><span data-stu-id="3e25b-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="3e25b-169">❓ **Wymaga orzeczenia: dodanie nowego pola wystąpienia do typu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="3e25b-170">Ta zmiana wpływa na serializację.</span><span class="sxs-lookup"><span data-stu-id="3e25b-170">This change impacts serialization.</span></span>

- <span data-ttu-id="3e25b-171">niedozwolone ❌ **: zmiana nazwy lub usunięcie publicznego elementu członkowskiego lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="3e25b-172">Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego elementu członkowskiego lub parametru.</span><span class="sxs-lookup"><span data-stu-id="3e25b-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="3e25b-173">Obejmuje to usunięcie lub zmianę nazwy metody pobierającej lub setter z właściwości, a także zmianę nazwy lub usunięcie elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="3e25b-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="3e25b-174">niedozwolone ❌ **: Dodawanie elementu członkowskiego do interfejsu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="3e25b-175">niedozwolone ❌ **: zmiana wartości stałej publicznej lub elementu członkowskiego wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="3e25b-176">niedozwolone ❌ **: zmiana typu właściwości, pola, parametru lub wartości zwracanej**</span><span class="sxs-lookup"><span data-stu-id="3e25b-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="3e25b-177">niedozwolone ❌ **: Dodawanie, usuwanie lub zmienianie kolejności parametrów**</span><span class="sxs-lookup"><span data-stu-id="3e25b-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="3e25b-178">niedozwolone ❌ **: Dodawanie lub usuwanie słowa kluczowego [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="3e25b-179">niedozwolone ❌ **: zmiana nazwy parametru (w tym zmiana jego wielkości liter)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="3e25b-180">Jest to uważane za rozdzielenie z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="3e25b-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="3e25b-181">Dzieli scenariusze z późnym wiązaniem, takie jak funkcja późnego wiązania w Visual Basic C#i [dynamiczna](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) w.</span><span class="sxs-lookup"><span data-stu-id="3e25b-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="3e25b-182">Jest ona podzielona na [zgodność źródłową](categories.md#source-compatibility) , gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="3e25b-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="3e25b-183">❌ **niedozwolone: zmiana z `ref` wartości zwracanej na `ref readonly` wartość zwracana**</span><span class="sxs-lookup"><span data-stu-id="3e25b-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="3e25b-184">niedozwolone ❌️ **: zmiana z `ref readonly` na `ref` wartość zwracana w wirtualnej metodzie lub interfejsie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="3e25b-185">niedozwolone ❌ **: Dodawanie lub usuwanie [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="3e25b-186">niedozwolone ❌ **: Usuwanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="3e25b-187">Chociaż często nie jest to istotna zmiana, C# ponieważ kompilator zamierza emitować instrukcje języka pośredniego (IL) elementu [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) do wywoływania metod niewirtualnych (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie jest), to zachowanie nie jest zmienne z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="3e25b-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="3e25b-188">C#nie jest jedynym językiem, który jest obiektem docelowym platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e25b-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="3e25b-189">C# Kompilator coraz bardziej próbuje zoptymalizować `callvirt` do normalnego wywołania, gdy metoda docelowa nie jest wirtualna i prawdopodobnie nie ma wartości null (na przykład metodę dostępną za pomocą [operatora propagacji?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span><span class="sxs-lookup"><span data-stu-id="3e25b-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="3e25b-190">Zastosowanie metody wirtualnej oznacza, że kod konsumenta często kończy wywoływanie go niepraktycznie.</span><span class="sxs-lookup"><span data-stu-id="3e25b-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="3e25b-191">niedozwolone ❌ **: Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="3e25b-192">niedozwolone ❌ **: wykonywanie abstrakcyjnej składowej wirtualnego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="3e25b-193">[Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zawiera implementację metody, która *może zostać* zastąpiona przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="3e25b-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="3e25b-194">[Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zawiera implementacji i *musi zostać* zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="3e25b-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="3e25b-195">niedozwolone ❌ **: Dodawanie abstrakcyjnej składowej do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory, które nie są [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="3e25b-196">niedozwolone ❌ **: Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="3e25b-197">niedozwolone ❌ **: Dodawanie przeciążenia, które wyklucza istniejące Przeciążenie i definiuje inne zachowanie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="3e25b-198">Spowoduje to przerwanie istniejących klientów, które zostały powiązane z poprzednim przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="3e25b-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="3e25b-199">Na przykład jeśli klasa ma jedną wersję metody, która akceptuje <xref:System.UInt32>, istniejący Klient pomyślnie powiąże się z tym przeciążeniem podczas przekazywania wartości <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="3e25b-200">Jednakże jeśli dodasz Przeciążenie, które akceptuje <xref:System.Int32>, podczas ponownego kompilowania lub korzystania z późnego wiązania, kompilator teraz tworzy powiązanie z nowym przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="3e25b-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="3e25b-201">W przypadku innych wyników zachowania jest to istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="3e25b-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="3e25b-202">niedozwolone ❌ **: Dodawanie konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrowego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="3e25b-203">niedozwolone ❌️ **: Dodawanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pola**</span><span class="sxs-lookup"><span data-stu-id="3e25b-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="3e25b-204">niedozwolone ❌ **: zmniejszanie widoczności elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="3e25b-205">Obejmuje to zmniejszenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy istnieją *dostępne* konstruktory (`public` lub `protected`), a typ *nie* jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md).</span><span class="sxs-lookup"><span data-stu-id="3e25b-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="3e25b-206">Jeśli tak się nie dzieje, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="3e25b-207">Zwiększenie widoczności elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="3e25b-208">niedozwolone ❌ **: zmiana typu elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="3e25b-209">Nie można zmodyfikować wartości zwracanej przez metodę lub typ właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="3e25b-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="3e25b-210">Na przykład sygnatura metody zwracającej <xref:System.Object> nie może zostać zmieniona w celu zwrócenia <xref:System.String>lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="3e25b-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="3e25b-211">niedozwolone ❌ **: Dodawanie pola do struktury, która wcześniej nie miała stanu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="3e25b-212">Określone reguły przypisywania umożliwiają użycie niezainicjowanych zmiennych, tak długo, jak typ zmiennej jest strukturą bezstanową.</span><span class="sxs-lookup"><span data-stu-id="3e25b-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="3e25b-213">Jeśli struktura jest stanowa, kod może kończyć się zainicjowanymi danymi.</span><span class="sxs-lookup"><span data-stu-id="3e25b-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="3e25b-214">Może to być zarówno uszkodzenie źródła, jak i uszkodzenie binarne.</span><span class="sxs-lookup"><span data-stu-id="3e25b-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="3e25b-215">niedozwolone ❌ **: wyzwalanie istniejącego zdarzenia, gdy wcześniej nie zostało ono wyzwolone**</span><span class="sxs-lookup"><span data-stu-id="3e25b-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="3e25b-216">Zmiany behawioralne</span><span class="sxs-lookup"><span data-stu-id="3e25b-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="3e25b-217">Zestawy</span><span class="sxs-lookup"><span data-stu-id="3e25b-217">Assemblies</span></span>

- <span data-ttu-id="3e25b-218">✔️ **dozwolone: Tworzenie zestawu przenośnego, gdy te same platformy są nadal obsługiwane**</span><span class="sxs-lookup"><span data-stu-id="3e25b-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="3e25b-219">niedozwolone ❌ **: zmiana nazwy zestawu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="3e25b-220">niedozwolone ❌ **: Zmiana klucza publicznego zestawu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="3e25b-221">Właściwości, pola, parametry i wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="3e25b-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="3e25b-222">✔️ **dozwolone: zmiana wartości właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na bardziej pochodny typ**</span><span class="sxs-lookup"><span data-stu-id="3e25b-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="3e25b-223">Na przykład Metoda zwracająca typ <xref:System.Object> może zwracać wystąpienie <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="3e25b-224">Nie można jednak zmienić sygnatury metody.)</span><span class="sxs-lookup"><span data-stu-id="3e25b-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="3e25b-225">✔️ **dozwolone: zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="3e25b-226">W czasie, gdy zakres wartości, które mogą być przesyłane do metody lub są zwracane przez element członkowski, można rozwinąć, parametr lub typ elementu członkowskiego nie mogą.</span><span class="sxs-lookup"><span data-stu-id="3e25b-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="3e25b-227">Na przykład, podczas gdy wartości przesyłane do metody mogą rozszerzać od 0-124 do 0-255, typ parametru nie może ulec zmianie z <xref:System.Byte> na <xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="3e25b-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="3e25b-228">niedozwolone ❌ **: zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="3e25b-229">Ta zmiana powoduje przerwanie istniejących przesłoniętych elementów członkowskich, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="3e25b-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="3e25b-230">niedozwolone ❌ **: zmniejszanie zakresu akceptowanych wartości dla właściwości lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="3e25b-231">niedozwolone ❌ **: zwiększenie zakresu zwracanych wartości dla właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3e25b-232">niedozwolone ❌ **: zmiana zwracanych wartości właściwości, pola, wartości zwracanej metody lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="3e25b-233">niedozwolone ❌ **: zmiana wartości domyślnej właściwości, pola lub parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="3e25b-234">niedozwolone ❌ **: zmiana dokładności liczbowej wartości zwracanej**</span><span class="sxs-lookup"><span data-stu-id="3e25b-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="3e25b-235">❓ **Wymaga orzeczenia: zmiana analizy danych wejściowych i zgłaszanie nowych wyjątków (nawet jeśli nie określono zachowania analizy w dokumentacji**</span><span class="sxs-lookup"><span data-stu-id="3e25b-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="3e25b-236">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="3e25b-236">Exceptions</span></span>

- <span data-ttu-id="3e25b-237">✔️ **dozwolone: Zgłaszanie bardziej pochodnego wyjątku niż istniejący wyjątek**</span><span class="sxs-lookup"><span data-stu-id="3e25b-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="3e25b-238">Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsłużył wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3e25b-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="3e25b-239">Na przykład w .NET Framework 4, metody tworzenia i pobierania kultur zaczęły zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException>, jeśli nie można odnaleźć kultury.</span><span class="sxs-lookup"><span data-stu-id="3e25b-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="3e25b-240">Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od <xref:System.ArgumentException>, jest to akceptowalna zmiana.</span><span class="sxs-lookup"><span data-stu-id="3e25b-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="3e25b-241">✔️ **dozwolone: Zgłaszanie bardziej szczegółowego wyjątku niż <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**</span><span class="sxs-lookup"><span data-stu-id="3e25b-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="3e25b-242">✔️ **dozwolone: Zgłaszanie wyjątku, który jest uznawany za niemożliwy do odzyskania**</span><span class="sxs-lookup"><span data-stu-id="3e25b-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="3e25b-243">Niemożliwy do odzyskania wyjątki nie powinny być przechwytywane, ale powinny być obsługiwane przez obsługę catch-all o wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="3e25b-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="3e25b-244">W związku z tym użytkownicy nie powinny mieć kodu, który przechwytuje te jawne wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3e25b-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="3e25b-245">Nieodwracalne wyjątki są następujące:</span><span class="sxs-lookup"><span data-stu-id="3e25b-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="3e25b-246">✔️ **dozwolone: Zgłaszanie nowego wyjątku w nowej ścieżce kodu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="3e25b-247">Wyjątek musi dotyczyć tylko nowej ścieżki kodu, która jest wykonywana z nowymi wartościami parametrów lub stanem, ale nie może zostać wykonana przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="3e25b-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="3e25b-248">✔️ **dozwolone: usuwanie wyjątku, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**</span><span class="sxs-lookup"><span data-stu-id="3e25b-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="3e25b-249">Na przykład Metoda `Divide`, która wcześniej obsługiwała tylko wartości dodatnie i wywołała <xref:System.ArgumentOutOfRangeException> w przeciwnym razie można zmienić, aby obsługiwała wartości ujemne i dodatnie bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="3e25b-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="3e25b-250">✔️ **dozwolone: Zmiana tekstu komunikatu o błędzie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="3e25b-251">Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się w zależności od kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="3e25b-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="3e25b-252">niedozwolone ❌ **: Zgłaszanie wyjątku w innym przypadku niewymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="3e25b-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="3e25b-253">niedozwolone ❌ **: usuwanie wyjątku w żadnym innym przypadku niewymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="3e25b-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="3e25b-254">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3e25b-254">Attributes</span></span>

- <span data-ttu-id="3e25b-255">✔️ **dozwolone: zmiana wartości atrybutu, który *nie* jest zauważalny**</span><span class="sxs-lookup"><span data-stu-id="3e25b-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="3e25b-256">❌ **niedozwolone: zmiana wartości atrybutu, który *jest* zauważalny**</span><span class="sxs-lookup"><span data-stu-id="3e25b-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="3e25b-257">❓ **Wymaga orzeczenia: usuwanie atrybutu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="3e25b-258">W większości przypadków usunięcie atrybutu (takiego jak <xref:System.NonSerializedAttribute>) jest istotną zmianą.</span><span class="sxs-lookup"><span data-stu-id="3e25b-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="3e25b-259">Obsługa platform</span><span class="sxs-lookup"><span data-stu-id="3e25b-259">Platform support</span></span>

- <span data-ttu-id="3e25b-260">✔️ **dozwolone: obsługa operacji na platformie, która była wcześniej nieobsługiwana**</span><span class="sxs-lookup"><span data-stu-id="3e25b-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="3e25b-261">niedozwolone ❌ **: nieobsługujące lub obecnie wymagający określonego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="3e25b-262">Wewnętrzne zmiany implementacji</span><span class="sxs-lookup"><span data-stu-id="3e25b-262">Internal implementation changes</span></span>

- <span data-ttu-id="3e25b-263">❓ **Wymaga orzeczenia: zmiana obszaru powierzchni typu wewnętrznego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="3e25b-264">Takie zmiany są zwykle dozwolone, chociaż przerywają odbicie prywatne.</span><span class="sxs-lookup"><span data-stu-id="3e25b-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3e25b-265">W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależą od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="3e25b-266">❓ **Wymaga orzeczenia: zmiana wewnętrznej implementacji elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="3e25b-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="3e25b-267">Te zmiany są ogólnie dozwolone, chociaż przerywają odbicie prywatne.</span><span class="sxs-lookup"><span data-stu-id="3e25b-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="3e25b-268">W niektórych przypadkach, gdzie kod klienta często zależy od odbicia prywatnego lub gdzie zmiana wprowadza niezamierzone efekty uboczne, te zmiany mogą być niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="3e25b-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="3e25b-269">✔️ **dozwolone: poprawa wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="3e25b-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="3e25b-270">Możliwość modyfikowania wydajności operacji jest istotna, ale takie zmiany mogą spowodować przerwanie kodu, który opiera się na bieżącej szybkości operacji.</span><span class="sxs-lookup"><span data-stu-id="3e25b-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="3e25b-271">Jest to szczególnie prawdziwe w przypadku kodu, który zależy od chronometrażu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="3e25b-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="3e25b-272">Zmiana wydajności nie powinna mieć wpływu na inne zachowanie interfejsu API. w przeciwnym razie zmiana zostanie przerwana.</span><span class="sxs-lookup"><span data-stu-id="3e25b-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="3e25b-273">✔️ **dozwolone: pośrednio (i często niekorzystnie) zmiana wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="3e25b-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="3e25b-274">Jeśli dana zmiana nie zostanie skategoryzowana z innego powodu, jest to dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="3e25b-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="3e25b-275">Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub dodając nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="3e25b-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="3e25b-276">Prawie zawsze ma to wpływ na wydajność, ale może być konieczne, aby interfejs API działał w oczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="3e25b-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="3e25b-277">niedozwolone ❌ **: zmiana synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**</span><span class="sxs-lookup"><span data-stu-id="3e25b-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="3e25b-278">Zmiany kodu</span><span class="sxs-lookup"><span data-stu-id="3e25b-278">Code changes</span></span>

- <span data-ttu-id="3e25b-279">✔️ **dozwolone: Dodawanie [parametrów](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="3e25b-280">❌ **niedozwolone: zmiana [struktury](../../csharp/language-reference/keywords/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**</span><span class="sxs-lookup"><span data-stu-id="3e25b-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/keywords/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="3e25b-281">niedozwolone ❌ **: Dodawanie słowa kluczowego [Checked](../../csharp/language-reference/keywords/virtual.md) do bloku kodu**</span><span class="sxs-lookup"><span data-stu-id="3e25b-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="3e25b-282">Ta zmiana może spowodować, że kod, który został wcześniej wykonany, aby zgłosić <xref:System.OverflowException> i jest nieakceptowalny.</span><span class="sxs-lookup"><span data-stu-id="3e25b-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="3e25b-283">niedozwolone ❌ **: Usuwanie [parametrów](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="3e25b-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="3e25b-284">niedozwolone ❌ **: zmiana kolejności, w której są uruchamiane zdarzenia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="3e25b-285">Deweloperzy mogą w rozsądny sposób oczekiwać, że wyzwalają zdarzenia w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="3e25b-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="3e25b-286">niedozwolone ❌ **: usuwanie podniesienia poziomu zdarzenia do danej akcji**</span><span class="sxs-lookup"><span data-stu-id="3e25b-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="3e25b-287">niedozwolone ❌ **: zmiana liczby przypadków, gdy są wywoływane zdarzenia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="3e25b-288">niedozwolone ❌ **: dodawanie <xref:System.FlagsAttribute> do typu wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="3e25b-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
