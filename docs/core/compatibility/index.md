---
title: Rodzaje przełomowych zmian
description: Dowiedz się, jak program .NET Core próbuje zachować zgodność deweloperów w wersjach .NET i jaki rodzaj zmiany jest uważany za przełomową zmianę.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628595"
---
# <a name="changes-that-affect-compatibility"></a><span data-ttu-id="9508b-103">Zmiany wpływające na zgodność</span><span class="sxs-lookup"><span data-stu-id="9508b-103">Changes that affect compatibility</span></span>

<span data-ttu-id="9508b-104">W całej swojej historii .NET próbował utrzymać wysoki poziom zgodności z wersji do wersji i różnych smaków .NET.</span><span class="sxs-lookup"><span data-stu-id="9508b-104">Throughout its history, .NET has attempted to maintain a high level of compatibility from version to version and across flavors of .NET.</span></span> <span data-ttu-id="9508b-105">To nadal dotyczy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9508b-105">This continues to be true for .NET Core.</span></span> <span data-ttu-id="9508b-106">Chociaż .NET Core można uznać za nową technologię, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość odejścia programu .NET Core od platformy .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9508b-106">Although .NET Core can be considered as a new technology that is independent of the .NET Framework, two major factors limit the ability of .NET Core to diverge from .NET Framework:</span></span>

- <span data-ttu-id="9508b-107">Duża liczba deweloperów pierwotnie opracowanych lub nadal rozwijać aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9508b-107">A large number of developers either originally developed or continue to develop .NET Framework applications.</span></span> <span data-ttu-id="9508b-108">Oczekują spójne zachowanie w implementacjach .NET.</span><span class="sxs-lookup"><span data-stu-id="9508b-108">They expect consistent behavior across .NET implementations.</span></span>

- <span data-ttu-id="9508b-109">Projekty biblioteki standardu .NET umożliwiają deweloperom tworzenie bibliotek docelowych dla typowych interfejsów API współużytkowane przez .NET Core i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9508b-109">.NET Standard library projects allow developers to create libraries that target common APIs shared by .NET Core and .NET Framework.</span></span> <span data-ttu-id="9508b-110">Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie jak ta sama biblioteka używana w aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9508b-110">Developers expect that a library used in a .NET Core application should behave identically to the same library used in a .NET Framework application.</span></span>

<span data-ttu-id="9508b-111">Wraz ze zgodnością w implementacjach .NET deweloperzy oczekują wysokiego poziomu zgodności w wersjach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9508b-111">Along with compatibility across .NET implementations, developers expect a high level of compatibility across .NET Core versions.</span></span> <span data-ttu-id="9508b-112">W szczególności kod napisany dla starszej wersji programu .NET Core powinien działać bezproblemowo w nowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9508b-112">In particular, code written for an earlier version of .NET Core should run seamlessly on a later version of .NET Core.</span></span> <span data-ttu-id="9508b-113">W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znalezione w nowo wydanych wersjach programu .NET Core powinny być również zgodne z wersjami wstępnymi, w których wprowadzono te interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="9508b-113">In fact, many developers expect that the new APIs found in newly released versions of .NET Core should also be compatible with the pre-release versions in which those APIs were introduced.</span></span>

<span data-ttu-id="9508b-114">W tym artykule opisano kategorie zmian zgodności (lub zmiany dotyczące podziału) oraz sposób, w jaki zespół .NET ocenia zmiany w każdej z tych kategorii.</span><span class="sxs-lookup"><span data-stu-id="9508b-114">This article outlines the categories of compatibility changes (or breaking changes) and the way in which the .NET team evaluates changes in each of these categories.</span></span> <span data-ttu-id="9508b-115">Zrozumienie, jak zespół platformy .NET podchodzi do możliwych zmian krytycznych, jest szczególnie przydatne dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [dotnet/runtime,](https://github.com/dotnet/runtime) które modyfikują zachowanie istniejących interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="9508b-115">Understanding how the .NET team approaches possible breaking changes is particularly helpful for developers who open pull requests in the [dotnet/runtime](https://github.com/dotnet/runtime) GitHub repository that modify the behavior of existing APIs.</span></span>

> [!NOTE]
> <span data-ttu-id="9508b-116">Aby uzyskać definicję kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi [wersjami,](categories.md)zobacz Kategorie zmian podziału .</span><span class="sxs-lookup"><span data-stu-id="9508b-116">For a definition of compatibility categories, such as binary compatibility and backward compatibility, see [Breaking change categories](categories.md).</span></span>

<span data-ttu-id="9508b-117">W poniższych sekcjach opisano kategorie zmian w interfejsach API .NET Core i ich wpływ na zgodność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9508b-117">The following sections describe the categories of changes made to .NET Core APIs and their impact on application compatibility.</span></span> <span data-ttu-id="9508b-118">Zmiany są dozwolone ✔️, ❌niedozwolone, lub wymagają oceny i oceny, jak przewidywalne, oczywiste i spójne poprzednie zachowanie było ❓.</span><span class="sxs-lookup"><span data-stu-id="9508b-118">Changes are either allowed ✔️, disallowed ❌, or require judgment and an evaluation of how predictable, obvious, and consistent the previous behavior was ❓.</span></span>

> [!NOTE]
> <span data-ttu-id="9508b-119">Oprócz wyświetlania jako przewodnik po tym, jak są oceniane zmiany w bibliotekach .NET Core, deweloperzy bibliotek mogą również używać tych kryteriów do oceny zmian w swoich bibliotekach, które są przeznaczone dla wielu implementacji i wersji .NET.</span><span class="sxs-lookup"><span data-stu-id="9508b-119">In addition to serving as a guide to how changes to .NET Core libraries are evaluated, library developers can also use these criteria to evaluate changes to their libraries that target multiple .NET implementations and versions.</span></span>

## <a name="modifications-to-the-public-contract"></a><span data-ttu-id="9508b-120">Zmiany w zamówień publicznych</span><span class="sxs-lookup"><span data-stu-id="9508b-120">Modifications to the public contract</span></span>

<span data-ttu-id="9508b-121">Zmiany w tej kategorii modyfikują publiczny obszar powierzchni typu.</span><span class="sxs-lookup"><span data-stu-id="9508b-121">Changes in this category modify the public surface area of a type.</span></span> <span data-ttu-id="9508b-122">Większość zmian w tej kategorii są niedozwolone, ponieważ naruszają *wsteczną zgodność* (zdolność aplikacji, która została opracowana z poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).</span><span class="sxs-lookup"><span data-stu-id="9508b-122">Most of the changes in this category are disallowed since they violate *backwards compatibility* (the ability of an application that was developed with a previous version of an API to execute without recompilation on a later version).</span></span>

### <a name="types"></a><span data-ttu-id="9508b-123">Typy</span><span class="sxs-lookup"><span data-stu-id="9508b-123">Types</span></span>

- <span data-ttu-id="9508b-124">✔️ **DOZWOLONE: Usuwanie implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**</span><span class="sxs-lookup"><span data-stu-id="9508b-124">✔️ **ALLOWED: Removing an interface implementation from a type when the interface is already implemented by a base type**</span></span>

- <span data-ttu-id="9508b-125">❓ **WYMAGA WYROKU: Dodawanie nowej implementacji interfejsu do typu**</span><span class="sxs-lookup"><span data-stu-id="9508b-125">❓ **REQUIRES JUDGMENT: Adding a new interface implementation to a type**</span></span>

  <span data-ttu-id="9508b-126">Jest to akceptowalna zmiana, ponieważ nie wpływa niekorzystnie na istniejących klientów.</span><span class="sxs-lookup"><span data-stu-id="9508b-126">This is an acceptable change because it does not adversely affect existing clients.</span></span> <span data-ttu-id="9508b-127">Wszelkie zmiany typu muszą działać w granicach dopuszczalnych zmian zdefiniowanych w tym miejscu, aby nowa implementacja pozostała możliwa do zaakceptowania.</span><span class="sxs-lookup"><span data-stu-id="9508b-127">Any changes to the type must work within the boundaries of acceptable changes defined here for the new implementation to remain acceptable.</span></span> <span data-ttu-id="9508b-128">Szczególna ostrożność jest konieczne podczas dodawania interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatora do generowania kodu lub danych, które nie mogą być używane w dół poziomu.</span><span class="sxs-lookup"><span data-stu-id="9508b-128">Extreme caution is necessary when adding interfaces that directly affect the ability of a designer or serializer to generate code or data that cannot be consumed down-level.</span></span> <span data-ttu-id="9508b-129">Przykładem jest <xref:System.Runtime.Serialization.ISerializable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="9508b-129">An example is the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>

- <span data-ttu-id="9508b-130">❓ **WYMAGA WYROKU: Wprowadzenie nowej klasy podstawowej**</span><span class="sxs-lookup"><span data-stu-id="9508b-130">❓ **REQUIRES JUDGMENT: Introducing a new base class**</span></span>

  <span data-ttu-id="9508b-131">Typ można wprowadzić do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmienić semantykę lub zachowanie istniejących typów.</span><span class="sxs-lookup"><span data-stu-id="9508b-131">A type can be introduced into a hierarchy between two existing types if it doesn't introduce any new [abstract](../../csharp/language-reference/keywords/abstract.md) members or change the semantics or behavior of existing types.</span></span> <span data-ttu-id="9508b-132">Na przykład w .NET Framework 2.0 <xref:System.Data.Common.DbConnection> klasa stała <xref:System.Data.SqlClient.SqlConnection>się nową klasą podstawową dla , która wcześniej pochodziła bezpośrednio z <xref:System.ComponentModel.Component>.</span><span class="sxs-lookup"><span data-stu-id="9508b-132">For example, in .NET Framework 2.0, the <xref:System.Data.Common.DbConnection> class became a new base class for <xref:System.Data.SqlClient.SqlConnection>, which had previously derived directly from <xref:System.ComponentModel.Component>.</span></span>

- <span data-ttu-id="9508b-133">✔️ **DOZWOLONE: Przenoszenie typu z jednego zespołu do drugiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-133">✔️ **ALLOWED: Moving a type from one assembly to another**</span></span>

  <span data-ttu-id="9508b-134">*Stary* zespół musi być <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> oznaczony, że wskazuje na nowy zespół.</span><span class="sxs-lookup"><span data-stu-id="9508b-134">The *old* assembly must be marked with the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> that points to the new assembly.</span></span>

- <span data-ttu-id="9508b-135">✔️ **DOZWOLONE: [struct](../../csharp/language-reference/builtin-types/struct.md) Zmiana typu struktury `readonly struct` na typ**</span><span class="sxs-lookup"><span data-stu-id="9508b-135">✔️ **ALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `readonly struct` type**</span></span>

  <span data-ttu-id="9508b-136">Zmiana `readonly struct` typu na `struct` typ jest niedozwolona.</span><span class="sxs-lookup"><span data-stu-id="9508b-136">Changing a `readonly struct` type to a `struct` type is not allowed.</span></span>

- <span data-ttu-id="9508b-137">✔️ **DOZWOLONE: Dodawanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu, gdy nie ma *dostępnych* (publicznych lub chronionych) konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="9508b-137">✔️ **ALLOWED: Adding the [sealed](../../csharp/language-reference/keywords/sealed.md) or [abstract](../../csharp/language-reference/keywords/abstract.md) keyword to a type when there are no *accessible* (public or protected) constructors**</span></span>

- <span data-ttu-id="9508b-138">✔️ **DOZWOLONE: Rozszerzenie widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="9508b-138">✔️ **ALLOWED: Expanding the visibility of a type**</span></span>

- <span data-ttu-id="9508b-139">❌**NIEDOZWOLONE: Zmiana obszaru nazw lub nazwy typu**</span><span class="sxs-lookup"><span data-stu-id="9508b-139">❌ **DISALLOWED: Changing the namespace or name of a type**</span></span>

- <span data-ttu-id="9508b-140">❌**NIEDOZWOLONE: Zmiana nazwy lub usunięcie typu publicznego**</span><span class="sxs-lookup"><span data-stu-id="9508b-140">❌ **DISALLOWED: Renaming or removing a public type**</span></span>

   <span data-ttu-id="9508b-141">Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.</span><span class="sxs-lookup"><span data-stu-id="9508b-141">This breaks all code that uses the renamed or removed type.</span></span>

- <span data-ttu-id="9508b-142">❌**NIEDOZWOLONE: Zmiana podstawowego typu wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="9508b-142">❌ **DISALLOWED: Changing the underlying type of an enumeration**</span></span>

   <span data-ttu-id="9508b-143">Jest to zmiana podziału czasu kompilacji i zachowania, a także zmiana podziału binarnego, która może sprawić, że argumenty atrybutów będą nierozłączne.</span><span class="sxs-lookup"><span data-stu-id="9508b-143">This is a compile-time and behavioral breaking change as well as a binary breaking change that can make attribute arguments unparsable.</span></span>

- <span data-ttu-id="9508b-144">❌**NIEDOZWOLONE: Uszczelnianie typu, który był wcześniej niezapieczętowany**</span><span class="sxs-lookup"><span data-stu-id="9508b-144">❌ **DISALLOWED: Sealing a type that was previously unsealed**</span></span>

- <span data-ttu-id="9508b-145">❌**NIEDOZWOLONE: Dodawanie interfejsu do zestawu typów podstawowych interfejsu**</span><span class="sxs-lookup"><span data-stu-id="9508b-145">❌ **DISALLOWED: Adding an interface to the set of base types of an interface**</span></span>

   <span data-ttu-id="9508b-146">Jeśli interfejs implementuje interfejs, który wcześniej nie zaimplementował, wszystkie typy, które zaimplementowane oryginalnej wersji interfejsu są przerwane.</span><span class="sxs-lookup"><span data-stu-id="9508b-146">If an interface implements an interface that it previously did not implement, all types that implemented the original version of the interface are broken.</span></span>

- <span data-ttu-id="9508b-147">❓ **WYMAGA WYROKU: Usunięcie klasy z zestawu klas podstawowych lub interfejsu z zestawu zaimplementowanych interfejsów**</span><span class="sxs-lookup"><span data-stu-id="9508b-147">❓ **REQUIRES JUDGMENT: Removing a class from the set of base classes or an interface from the set of implemented interfaces**</span></span>

  <span data-ttu-id="9508b-148">Istnieje jeden wyjątek od reguły usuwania interfejsu: można dodać implementację interfejsu, który pochodzi z usuniętego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9508b-148">There is one exception to the rule for interface removal: you can add the implementation of an interface that derives from the removed interface.</span></span> <span data-ttu-id="9508b-149">Na przykład można <xref:System.IDisposable> usunąć, jeśli typ lub <xref:System.ComponentModel.IComponent>interfejs teraz <xref:System.IDisposable>implementuje , który implementuje .</span><span class="sxs-lookup"><span data-stu-id="9508b-149">For example, you can remove <xref:System.IDisposable> if the type or interface now implements <xref:System.ComponentModel.IComponent>, which implements <xref:System.IDisposable>.</span></span>

- <span data-ttu-id="9508b-150">❌\*\*NIEDOZWOLONE: Zmiana `readonly struct` typu na typ [struktury](../../csharp/language-reference/builtin-types/struct.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-150">❌ **DISALLOWED: Changing a `readonly struct` type to a [struct](../../csharp/language-reference/builtin-types/struct.md) type**</span></span>

  <span data-ttu-id="9508b-151">Zmiana `struct` typu na typ `readonly struct` jest jednak dozwolona.</span><span class="sxs-lookup"><span data-stu-id="9508b-151">The change of a `struct` type to a `readonly struct` type is allowed, however.</span></span>

- <span data-ttu-id="9508b-152">❌**NIEDOZWOLONE: Zmiana typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `ref struct` typ i na odwrót**</span><span class="sxs-lookup"><span data-stu-id="9508b-152">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) type to a `ref struct` type, and vice versa**</span></span>

- <span data-ttu-id="9508b-153">❌**NIEDOZWOLONE: Zmniejszenie widoczności typu**</span><span class="sxs-lookup"><span data-stu-id="9508b-153">❌ **DISALLOWED: Reducing the visibility of a type**</span></span>

   <span data-ttu-id="9508b-154">Jednak zwiększenie widoczności typu jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-154">However, increasing the visibility of a type is allowed.</span></span>

### <a name="members"></a><span data-ttu-id="9508b-155">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9508b-155">Members</span></span>

- <span data-ttu-id="9508b-156">✔️ \*\*DOZWOLONE: Rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-156">✔️ **ALLOWED: Expanding the visibility of a member that is not [virtual](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9508b-157">✔️ \*\*DOZWOLONE: Dodawanie abstrakcyjnego elementu członkowskiego do typu publicznego, który nie ma *dostępnych* (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-157">✔️ **ALLOWED: Adding an abstract member to a public type that has no *accessible* (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

  <span data-ttu-id="9508b-158">Jednak dodanie abstrakcyjnego elementu członkowskiego do typu, który ma dostępne `sealed` (publiczne lub chronione) konstruktory i nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-158">However, adding an abstract member to a type that has accessible (public or protected) constructors and is not `sealed` is not allowed.</span></span>

- <span data-ttu-id="9508b-159">✔️ \*\*DOZWOLONE: Ograniczenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-159">✔️ **ALLOWED: Restricting the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when the type has no accessible (public or protected) constructors, or the type is [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9508b-160">✔️ **DOZWOLONE: Przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**</span><span class="sxs-lookup"><span data-stu-id="9508b-160">✔️ **ALLOWED: Moving a member into a class higher in the hierarchy than the type from which it was removed**</span></span>

- <span data-ttu-id="9508b-161">✔️ **DOZWOLONE: Dodawanie lub usuwanie zastąpienia**</span><span class="sxs-lookup"><span data-stu-id="9508b-161">✔️ **ALLOWED: Adding or removing an override**</span></span>

  <span data-ttu-id="9508b-162">Wprowadzenie zastąpienia może spowodować, że poprzedni konsumenci przesunęli się przez zastąpienie podczas wywoływania [bazy](../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="9508b-162">Introducing an override might cause previous consumers to skip over the override when calling [base](../../csharp/language-reference/keywords/base.md).</span></span>

- <span data-ttu-id="9508b-163">✔️ **DOZWOLONE: Dodawanie konstruktora do klasy wraz z konstruktorem bezparametrów, jeśli klasa wcześniej nie miała konstruktorów**</span><span class="sxs-lookup"><span data-stu-id="9508b-163">✔️ **ALLOWED: Adding a constructor to a class, along with a parameterless constructor if the class previously had no constructors**</span></span>

   <span data-ttu-id="9508b-164">Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrów, nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-164">However, adding a constructor to a class that previously had no constructors *without* adding the parameterless constructor is not allowed.</span></span>

- <span data-ttu-id="9508b-165">✔️ \*\*DOZWOLONE: Zmiana elementu członkowskiego z [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) na [wirtualny](../../csharp/language-reference/keywords/virtual.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-165">✔️ **ALLOWED: Changing a member from [abstract](../../csharp/language-reference/keywords/abstract.md) to [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

- <span data-ttu-id="9508b-166">✔️ **DOZWOLONE: Zmiana `ref readonly` wartości `ref` zwracanej na wartość (z wyjątkiem metod wirtualnych lub interfejsów)**</span><span class="sxs-lookup"><span data-stu-id="9508b-166">✔️ **ALLOWED: Changing from a `ref readonly` to a `ref` return value (except for virtual methods or interfaces)**</span></span>

- <span data-ttu-id="9508b-167">✔️ **DOZWOLONE: Usuwanie [tylko odczytu](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest typem wartości zapisywanych**</span><span class="sxs-lookup"><span data-stu-id="9508b-167">✔️ **ALLOWED: Removing [readonly](../../csharp/language-reference/keywords/readonly.md) from a field, unless the static type of the field is a mutable value type**</span></span>

- <span data-ttu-id="9508b-168">✔️ **DOZWOLONE: wywoływanie nowego zdarzenia, które nie było wcześniej zdefiniowane**</span><span class="sxs-lookup"><span data-stu-id="9508b-168">✔️ **ALLOWED: Calling a new event that wasn't previously defined**</span></span>

- <span data-ttu-id="9508b-169">❓ **WYMAGA WYROKU: Dodawanie nowego pola instancji do typu**</span><span class="sxs-lookup"><span data-stu-id="9508b-169">❓ **REQUIRES JUDGMENT: Adding a new instance field to a type**</span></span>

   <span data-ttu-id="9508b-170">Ta zmiana ma wpływ na serializację.</span><span class="sxs-lookup"><span data-stu-id="9508b-170">This change impacts serialization.</span></span>

- <span data-ttu-id="9508b-171">❌**NIEDOZWOLONE: Zmiana nazwy lub usunięcie publicznego elementu członkowskiego lub parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-171">❌ **DISALLOWED: Renaming or removing a public member or parameter**</span></span>

   <span data-ttu-id="9508b-172">Spowoduje to przerwanie całego kodu, który używa zmienionego lub usuniętego elementu członkowskiego lub parametru.</span><span class="sxs-lookup"><span data-stu-id="9508b-172">This breaks all code that uses the renamed or removed member, or parameter.</span></span>

   <span data-ttu-id="9508b-173">Obejmuje to usunięcie lub zmianę nazwy getter lub setter z właściwości, a także zmiana nazwy lub usunięcie elementów członkowskich wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="9508b-173">This includes removing or renaming a getter or setter from a property, as well as renaming or removing enumeration members.</span></span>

- <span data-ttu-id="9508b-174">❌**NIEDOZWOLONE: Dodawanie elementu członkowskiego do interfejsu**</span><span class="sxs-lookup"><span data-stu-id="9508b-174">❌ **DISALLOWED: Adding a member to an interface**</span></span>

- <span data-ttu-id="9508b-175">❌**NIEDOZWOLONE: Zmiana wartości elementu członkowskiego stałej publicznej lub wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="9508b-175">❌ **DISALLOWED: Changing the value of a public constant or enumeration member**</span></span>

- <span data-ttu-id="9508b-176">❌**NIEDOZWOLONE: Zmiana typu właściwości, pola, parametru lub wartości zwracanej**</span><span class="sxs-lookup"><span data-stu-id="9508b-176">❌ **DISALLOWED: Changing the type of a property, field, parameter, or return value**</span></span>

- <span data-ttu-id="9508b-177">❌**NIEDOZWOLONE: Dodawanie, usuwanie lub zmienianie kolejności parametrów**</span><span class="sxs-lookup"><span data-stu-id="9508b-177">❌ **DISALLOWED: Adding, removing, or changing the order of parameters**</span></span>

- <span data-ttu-id="9508b-178">❌**NIEDOZWOLONE: Dodawanie lub usuwanie [słowa](../../csharp/language-reference/keywords/in.md)kluczowego in , [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-178">❌ **DISALLOWED: Adding or removing the [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) , or [ref](../../csharp/language-reference/keywords/ref.md) keyword from a parameter**</span></span>

- <span data-ttu-id="9508b-179">❌**NIEDOZWOLONE: Zmiana nazwy parametru (w tym zmiana jego przypadku)**</span><span class="sxs-lookup"><span data-stu-id="9508b-179">❌ **DISALLOWED: Renaming a parameter (including changing its case)**</span></span>

  <span data-ttu-id="9508b-180">Jest to uważane za złamanie z dwóch powodów:</span><span class="sxs-lookup"><span data-stu-id="9508b-180">This is considered breaking for two reasons:</span></span>

  - <span data-ttu-id="9508b-181">Przerywa scenariusze późnego wiązania, takie jak funkcja późnego wiązania w języku Visual Basic i [dynamiczna](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9508b-181">It breaks late-bound scenarios such as the late binding feature in Visual Basic and [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) in C#.</span></span>

  - <span data-ttu-id="9508b-182">Przerywa [zgodność źródła,](categories.md#source-compatibility) gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span><span class="sxs-lookup"><span data-stu-id="9508b-182">It breaks [source compatibility](categories.md#source-compatibility) when developers use [named arguments](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).</span></span>

- <span data-ttu-id="9508b-183">❌**NIEDOZWOLONE: Zmiana wartości `ref` zwracanej `ref readonly` na wartość zwracaną**</span><span class="sxs-lookup"><span data-stu-id="9508b-183">❌ **DISALLOWED: Changing from a `ref` return value to a `ref readonly` return value**</span></span>

- <span data-ttu-id="9508b-184">❌️**NIEDOZWOLONE: Zmiana wartości `ref readonly` zwracanej `ref` na wirtualną metodę lub interfejs**</span><span class="sxs-lookup"><span data-stu-id="9508b-184">❌️ **DISALLOWED: Changing from a `ref readonly` to a `ref` return value on a virtual method or interface**</span></span>

- <span data-ttu-id="9508b-185">❌**NIEDOZWOLONE: Dodawanie lub usuwanie [streszczenia](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-185">❌ **DISALLOWED: Adding or removing [abstract](../../csharp/language-reference/keywords/abstract.md) from a member**</span></span>

- <span data-ttu-id="9508b-186">❌**NIEDOZWOLONE: Usuwanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-186">❌ **DISALLOWED: Removing the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword from a member**</span></span>

  <span data-ttu-id="9508b-187">Chociaż często nie jest to zmiana podziału, ponieważ kompilator Języka C#ma tendencję do emitowania [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) języka pośredniego (IL) instrukcje do wywołania metod innych niż wirtualne (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie), to zachowanie nie jest zmienna z kilku powodów:</span><span class="sxs-lookup"><span data-stu-id="9508b-187">While this often is not a breaking change because the C# compiler tends to emit [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) Intermediate Language (IL) instructions to call non-virtual methods (`callvirt` performs a null check, while a normal call doesn't), this behavior is not invariable for several reasons:</span></span>
  - <span data-ttu-id="9508b-188">C# nie jest jedynym językiem, który .</span><span class="sxs-lookup"><span data-stu-id="9508b-188">C# is not the only language that .NET targets.</span></span>

  - <span data-ttu-id="9508b-189">Kompilator Języka C# `callvirt` coraz częściej próbuje zoptymalizować do normalnego wywołania, gdy metoda docelowa nie jest wirtualny i prawdopodobnie nie jest null (na przykład metoda dostępna za pośrednictwem [?. null propagacji operatora).](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="9508b-189">The C# compiler increasingly tries to optimize `callvirt` to a normal call whenever the target method is non-virtual and is probably not null (such as a method accessed through the [?. null propagation operator](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).</span></span>

  <span data-ttu-id="9508b-190">Tworzenie metody wirtualnej oznacza, że kod konsumenta często kończy się wywołanie go nie-praktycznie.</span><span class="sxs-lookup"><span data-stu-id="9508b-190">Making a method virtual means that the consumer code would often end up calling it non-virtually.</span></span>

- <span data-ttu-id="9508b-191">❌**NIEDOZWOLONE: Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do członka**</span><span class="sxs-lookup"><span data-stu-id="9508b-191">❌ **DISALLOWED: Adding the [virtual](../../csharp/language-reference/keywords/virtual.md) keyword to a member**</span></span>

- <span data-ttu-id="9508b-192">❌**NIEDOZWOLONE: Tworzenie abstrakcyjnego elementu wirtualnego**</span><span class="sxs-lookup"><span data-stu-id="9508b-192">❌ **DISALLOWED: Making a virtual member abstract**</span></span>

  <span data-ttu-id="9508b-193">[Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zapewnia implementację metody, które *mogą być* zastąpione przez klasę pochodną.</span><span class="sxs-lookup"><span data-stu-id="9508b-193">A [virtual member](../../csharp/language-reference/keywords/virtual.md) provides a method implementation that *can be* overridden by a derived class.</span></span> <span data-ttu-id="9508b-194">[Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zapewnia implementacji i *musi zostać* zastąpiony.</span><span class="sxs-lookup"><span data-stu-id="9508b-194">An [abstract member](../../csharp/language-reference/keywords/abstract.md) provides no implementation and *must be* overridden.</span></span>

- <span data-ttu-id="9508b-195">❌\*\*NIEDOZWOLONE: Dodawanie abstrakcyjnego elementu członkowskiego do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory i który nie jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-195">❌ **DISALLOWED: Adding an abstract member to a public type that has accessible (public or protected) constructors and that is not [sealed](../../csharp/language-reference/keywords/sealed.md)**</span></span>

- <span data-ttu-id="9508b-196">❌**NIEDOZWOLONE: Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-196">❌ **DISALLOWED: Adding or removing the [static](../../csharp/language-reference/keywords/static.md) keyword from a member**</span></span>

- <span data-ttu-id="9508b-197">❌**NIEDOZWOLONE: Dodawanie przeciążenia, które wyklucza istniejące przeciążenie i definiuje inne zachowanie**</span><span class="sxs-lookup"><span data-stu-id="9508b-197">❌ **DISALLOWED: Adding an overload that precludes an existing overload and defines a different behavior**</span></span>

  <span data-ttu-id="9508b-198">Spowoduje to przerwanie istniejących klientów, które były powiązane z poprzednim przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="9508b-198">This breaks existing clients that were bound to the previous overload.</span></span> <span data-ttu-id="9508b-199">Na przykład jeśli klasa ma jedną wersję <xref:System.UInt32>metody, która akceptuje , istniejący konsument pomyślnie powiąże <xref:System.Int32> się z tym przeciążeniem podczas przekazywania wartości.</span><span class="sxs-lookup"><span data-stu-id="9508b-199">For example, if a class has a single version of a method that accepts a <xref:System.UInt32>, an existing consumer will successfully bind to that overload when passing a <xref:System.Int32> value.</span></span> <span data-ttu-id="9508b-200">Jednak jeśli dodasz przeciążenie, <xref:System.Int32>które akceptuje , podczas ponownej kompilacji lub przy użyciu późnego wiązania, kompilator teraz wiąże się z nowym przeciążeniem.</span><span class="sxs-lookup"><span data-stu-id="9508b-200">However, if you add an overload that accepts an <xref:System.Int32>, when recompiling or using late-binding, the compiler now binds to the new overload.</span></span> <span data-ttu-id="9508b-201">Jeśli różne wyniki zachowania, jest to zmiana podziału.</span><span class="sxs-lookup"><span data-stu-id="9508b-201">If different behavior results, this is a breaking change.</span></span>

- <span data-ttu-id="9508b-202">❌**NIEDOZWOLONE: Dodawanie konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrów**</span><span class="sxs-lookup"><span data-stu-id="9508b-202">❌ **DISALLOWED: Adding a constructor to a class that previously had no constructor without adding the parameterless constructor**</span></span>

- <span data-ttu-id="9508b-203">❌️**NIEDOZWOLONE: Dodawanie tylko do [odczytu](../../csharp/language-reference/keywords/readonly.md) do pola**</span><span class="sxs-lookup"><span data-stu-id="9508b-203">❌️ **DISALLOWED: Adding [readonly](../../csharp/language-reference/keywords/readonly.md) to a field**</span></span>

- <span data-ttu-id="9508b-204">❌**NIEDOZWOLONE: Zmniejszenie widoczności elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-204">❌ **DISALLOWED: Reducing the visibility of a member**</span></span>

   <span data-ttu-id="9508b-205">Obejmuje to zmniejszenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego,`public` `protected`gdy istnieją *dostępne* (lub) konstruktory, a typ *nie* jest [zapieczętowany.](../../csharp/language-reference/keywords/sealed.md)</span><span class="sxs-lookup"><span data-stu-id="9508b-205">This includes reducing the visibility of a [protected](../../csharp/language-reference/keywords/protected.md) member when there are *accessible* (`public` or `protected`) constructors and the type is *not* [sealed](../../csharp/language-reference/keywords/sealed.md).</span></span> <span data-ttu-id="9508b-206">Jeśli tak nie jest, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-206">If this is not the case, reducing the visibility of a protected member is allowed.</span></span>

   <span data-ttu-id="9508b-207">Zwiększenie widoczności elementu członkowskiego jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-207">Increasing the visibility of a member is allowed.</span></span>

- <span data-ttu-id="9508b-208">❌**NIEDOZWOLONE: Zmiana typu elementu członkowskiego**</span><span class="sxs-lookup"><span data-stu-id="9508b-208">❌ **DISALLOWED: Changing the type of a member**</span></span>

   <span data-ttu-id="9508b-209">Nie można zmodyfikować wartości zwracanej metody lub typu właściwości lub pola.</span><span class="sxs-lookup"><span data-stu-id="9508b-209">The return value of a method or the type of a property or field cannot be modified.</span></span> <span data-ttu-id="9508b-210">Na przykład podpis metody, która <xref:System.Object> zwraca nie można <xref:System.String>zmienić, aby zwrócić , lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="9508b-210">For example, the signature of a method that returns an <xref:System.Object> cannot be changed to return a <xref:System.String>, or vice versa.</span></span>

- <span data-ttu-id="9508b-211">❌**NIEDOZWOLONE: Dodawanie pola do struktury, która wcześniej nie miała żadnego stanu**</span><span class="sxs-lookup"><span data-stu-id="9508b-211">❌ **DISALLOWED: Adding a field to a struct that previously had no state**</span></span>

  <span data-ttu-id="9508b-212">Reguły przypisania określonego zezwalają na używanie zmiennych niezainicjowanych, o ile typ zmiennej jest strukturą bezstanową.</span><span class="sxs-lookup"><span data-stu-id="9508b-212">Definite assignment rules allow the use of uninitialized variables so long as the variable type is a stateless struct.</span></span> <span data-ttu-id="9508b-213">Jeśli struktura jest stanowa, kod może skończyć się z niezainicjowanych danych.</span><span class="sxs-lookup"><span data-stu-id="9508b-213">If the struct is made stateful, code could end up with uninitialized data.</span></span> <span data-ttu-id="9508b-214">Jest to zarówno potencjalnie źródło zerwania i binarnych zmian podziału.</span><span class="sxs-lookup"><span data-stu-id="9508b-214">This is both potentially a source breaking and a binary breaking change.</span></span>

- <span data-ttu-id="9508b-215">❌**NIEDOZWOLONE: Wypalanie istniejącego zdarzenia, gdy nigdy nie zostało odpalone przed**</span><span class="sxs-lookup"><span data-stu-id="9508b-215">❌ **DISALLOWED: Firing an existing event when it was never fired before**</span></span>

## <a name="behavioral-changes"></a><span data-ttu-id="9508b-216">Zmiany w zachowaniu</span><span class="sxs-lookup"><span data-stu-id="9508b-216">Behavioral changes</span></span>

### <a name="assemblies"></a><span data-ttu-id="9508b-217">Zestawy</span><span class="sxs-lookup"><span data-stu-id="9508b-217">Assemblies</span></span>

- <span data-ttu-id="9508b-218">✔️ **DOZWOLONE: Wykonywanie przenośnego montażu, gdy te same platformy są nadal obsługiwane**</span><span class="sxs-lookup"><span data-stu-id="9508b-218">✔️ **ALLOWED: Making an assembly portable when the same platforms are still supported**</span></span>

- <span data-ttu-id="9508b-219">❌**NIEDOZWOLONE: Zmiana nazwy zestawu**</span><span class="sxs-lookup"><span data-stu-id="9508b-219">❌ **DISALLOWED: Changing the name of an assembly**</span></span>
- <span data-ttu-id="9508b-220">❌**NIEDOZWOLONE: Zmiana klucza publicznego zestawu**</span><span class="sxs-lookup"><span data-stu-id="9508b-220">❌ **DISALLOWED: Changing the public key of an assembly**</span></span>

### <a name="properties-fields-parameters-and-return-values"></a><span data-ttu-id="9508b-221">Właściwości, pola, parametry i wartości zwracane</span><span class="sxs-lookup"><span data-stu-id="9508b-221">Properties, fields, parameters, and return values</span></span>

- <span data-ttu-id="9508b-222">✔️ **DOZWOLONE: Zmiana wartości właściwości, pola, wartości zwracanej lub [parametru out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na typ bardziej pochodny**</span><span class="sxs-lookup"><span data-stu-id="9508b-222">✔️ **ALLOWED: Changing the value of a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter to a more derived type**</span></span>

  <span data-ttu-id="9508b-223">Na przykład metoda, która zwraca <xref:System.Object> typ <xref:System.String> może zwrócić wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9508b-223">For example, a method that returns a type of <xref:System.Object> can return a <xref:System.String> instance.</span></span> <span data-ttu-id="9508b-224">(Jednak podpis metody nie może ulec zmianie).</span><span class="sxs-lookup"><span data-stu-id="9508b-224">(However, the method signature cannot change.)</span></span>

- <span data-ttu-id="9508b-225">✔️ **DOZWOLONE: Zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element [członkowski](../../csharp/language-reference/keywords/virtual.md) nie jest wirtualny**</span><span class="sxs-lookup"><span data-stu-id="9508b-225">✔️ **ALLOWED: Increasing the range of accepted values for a property or parameter if the member is not [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

  <span data-ttu-id="9508b-226">Podczas gdy zakres wartości, które mogą być przekazywane do metody lub są zwracane przez element członkowski można rozwinąć, parametr lub typ elementu członkowskiego nie może.</span><span class="sxs-lookup"><span data-stu-id="9508b-226">While the range of values that can be passed to the method or are returned by the member can expand, the parameter or member type cannot.</span></span> <span data-ttu-id="9508b-227">Na przykład, podczas gdy wartości przekazywane do metody można rozwinąć od 0-124 do <xref:System.Byte> 0-255, typ parametru nie można zmienić z . <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="9508b-227">For example, while the values passed to a method can expand from 0-124 to 0-255, the parameter type cannot change from <xref:System.Byte> to <xref:System.Int32>.</span></span>

- <span data-ttu-id="9508b-228">❌**NIEDOZWOLONE: Zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element [członkowski](../../csharp/language-reference/keywords/virtual.md) jest wirtualny**</span><span class="sxs-lookup"><span data-stu-id="9508b-228">❌ **DISALLOWED: Increasing the range of accepted values for a property or parameter if the member is [virtual](../../csharp/language-reference/keywords/virtual.md)**</span></span>

   <span data-ttu-id="9508b-229">Ta zmiana przerywa istniejące elementy nadrzędnego, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.</span><span class="sxs-lookup"><span data-stu-id="9508b-229">This change breaks existing overridden members, which will not function correctly for the extended range of values.</span></span>

- <span data-ttu-id="9508b-230">❌**NIEDOZWOLONE: Zmniejszenie zakresu akceptowanych wartości dla właściwości lub parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-230">❌ **DISALLOWED: Decreasing the range of accepted values for a property or parameter**</span></span>

- <span data-ttu-id="9508b-231">❌\*\*NIEDOZWOLONE: Zwiększenie zakresu zwracanych wartości dla parametru właściwości, pola, wartości zwracanej lub [wychodzącej](../../csharp/language-reference/keywords/out-parameter-modifier.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-231">❌ **DISALLOWED: Increasing the range of returned values for a property, field, return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="9508b-232">❌\*\*NIEDOZWOLONE: Zmiana zwracanych wartości dla właściwości, pola, wartości zwracanej metody lub [parametru out](../../csharp/language-reference/keywords/out-parameter-modifier.md) \*\*</span><span class="sxs-lookup"><span data-stu-id="9508b-232">❌ **DISALLOWED: Changing the returned values for a property, field, method return value, or [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) parameter**</span></span>

- <span data-ttu-id="9508b-233">❌**NIEDOZWOLONE: Zmiana wartości domyślnej właściwości, pola lub parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-233">❌ **DISALLOWED: Changing the default value of a property, field, or parameter**</span></span>

- <span data-ttu-id="9508b-234">❌**NIEDOZWOLONE: Zmiana dokładności wartości zwracanej liczbowej**</span><span class="sxs-lookup"><span data-stu-id="9508b-234">❌ **DISALLOWED: Changing the precision of a numeric return value**</span></span>

- <span data-ttu-id="9508b-235">❓ **WYMAGA WYROKU: Zmiana w analizowaniu danych wejściowych i zgłaszaniu nowych wyjątków (nawet jeśli zachowanie analizy nie jest określone w dokumentacji**</span><span class="sxs-lookup"><span data-stu-id="9508b-235">❓ **REQUIRES JUDGMENT: A change in the parsing of input and throwing new exceptions (even if parsing behavior is not specified in the documentation**</span></span>

### <a name="exceptions"></a><span data-ttu-id="9508b-236">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9508b-236">Exceptions</span></span>

- <span data-ttu-id="9508b-237">✔️ **DOZWOLONE: Zgłaszanie wyjątku bardziej pochodnego niż istniejący wyjątek**</span><span class="sxs-lookup"><span data-stu-id="9508b-237">✔️ **ALLOWED: Throwing a more derived exception than an existing exception**</span></span>

  <span data-ttu-id="9508b-238">Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsługuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9508b-238">Because the new exception is a subclass of an existing exception, previous exception handling code continues to handle the exception.</span></span> <span data-ttu-id="9508b-239">Na przykład w .NET Framework 4 metody tworzenia i pobierania <xref:System.Globalization.CultureNotFoundException> kultury <xref:System.ArgumentException> zaczęły zgłaszać zamiast if kultury nie można odnaleźć.</span><span class="sxs-lookup"><span data-stu-id="9508b-239">For example, in .NET Framework 4, culture creation and retrieval methods began to throw a <xref:System.Globalization.CultureNotFoundException> instead of an <xref:System.ArgumentException> if the culture could not be found.</span></span> <span data-ttu-id="9508b-240">Ponieważ <xref:System.Globalization.CultureNotFoundException> wywodzi się z <xref:System.ArgumentException>, jest to akceptowalna zmiana.</span><span class="sxs-lookup"><span data-stu-id="9508b-240">Because <xref:System.Globalization.CultureNotFoundException> derives from <xref:System.ArgumentException>, this is an acceptable change.</span></span>

- <span data-ttu-id="9508b-241">✔️ **DOZWOLONE: Rzucanie bardziej szczegółowy <xref:System.NotSupportedException> <xref:System.NotImplementedException>wyjątek <xref:System.NullReferenceException> niż ,**</span><span class="sxs-lookup"><span data-stu-id="9508b-241">✔️ **ALLOWED: Throwing a more specific exception than <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**</span></span>

- <span data-ttu-id="9508b-242">✔️ **DOZWOLONE: Zgłaszanie wyjątku, który jest uważany za nieodwracalny**</span><span class="sxs-lookup"><span data-stu-id="9508b-242">✔️ **ALLOWED: Throwing an exception that is considered unrecoverable**</span></span>

  <span data-ttu-id="9508b-243">Nieodwracalne wyjątki nie powinny być przechwycone, ale zamiast tego powinny być obsługiwane przez program obsługi catch-all wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="9508b-243">Unrecoverable exceptions should not be caught but instead should be handled by a high-level catch-all handler.</span></span> <span data-ttu-id="9508b-244">W związku z tym użytkownicy nie powinni mieć kod, który przechwytuje te jawne wyjątki.</span><span class="sxs-lookup"><span data-stu-id="9508b-244">Therefore, users are not expected to have code that catches these explicit exceptions.</span></span> <span data-ttu-id="9508b-245">Nieodwracalne wyjątki to:</span><span class="sxs-lookup"><span data-stu-id="9508b-245">The unrecoverable exceptions are:</span></span>

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- <span data-ttu-id="9508b-246">✔️ **DOZWOLONE: Zgłaszanie nowego wyjątku w nowej ścieżce kodu**</span><span class="sxs-lookup"><span data-stu-id="9508b-246">✔️ **ALLOWED: Throwing a new exception in a new code path**</span></span>

  <span data-ttu-id="9508b-247">Wyjątek musi mieć zastosowanie tylko do nowej ścieżki kodu, który jest wykonywany z nowych wartości parametrów lub stanu i które nie mogą być wykonywane przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="9508b-247">The exception must apply only to a new code-path that's executed with new parameter values or state and that can't be executed by existing code that targets the previous version.</span></span>

- <span data-ttu-id="9508b-248">✔️ **DOZWOLONE: Usuwanie wyjątku, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**</span><span class="sxs-lookup"><span data-stu-id="9508b-248">✔️ **ALLOWED: Removing an exception to enable more robust behavior or new scenarios**</span></span>

  <span data-ttu-id="9508b-249">Na przykład `Divide` metoda, która wcześniej obsługiwała <xref:System.ArgumentOutOfRangeException> tylko wartości dodatnie i w przeciwnym razie, może zostać zmieniona w celu obsługi wartości ujemnych i dodatnich bez zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9508b-249">For example, a `Divide` method that previously only handled positive values and threw an <xref:System.ArgumentOutOfRangeException> otherwise can be changed to support both negative and positive values without throwing an exception.</span></span>

- <span data-ttu-id="9508b-250">✔️ **DOZWOLONE: Zmiana tekstu komunikatu o błędzie**</span><span class="sxs-lookup"><span data-stu-id="9508b-250">✔️ **ALLOWED: Changing the text of an error message**</span></span>

  <span data-ttu-id="9508b-251">Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się na podstawie kultury użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9508b-251">Developers should not rely on the text of error messages, which also change based on the user's culture.</span></span>

- <span data-ttu-id="9508b-252">❌**NIEDOZWOLONE: Zgłaszanie wyjątku w każdym innym przypadku nie wymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="9508b-252">❌ **DISALLOWED: Throwing an exception in any other case not listed above**</span></span>

- <span data-ttu-id="9508b-253">❌**NIEDOZWOLONE: Usuwanie wyjątku w każdym innym przypadku niewymienionym powyżej**</span><span class="sxs-lookup"><span data-stu-id="9508b-253">❌ **DISALLOWED: Removing an exception in any other case not listed above**</span></span>

### <a name="attributes"></a><span data-ttu-id="9508b-254">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9508b-254">Attributes</span></span>

- <span data-ttu-id="9508b-255">✔️ **DOZWOLONE: Zmiana wartości atrybutu, który *nie* jest obserwowalny**</span><span class="sxs-lookup"><span data-stu-id="9508b-255">✔️ **ALLOWED: Changing the value of an attribute that is *not* observable**</span></span>

- <span data-ttu-id="9508b-256">❌**NIEDOZWOLONE: Zmiana wartości atrybutu, który *jest* obserwowalny**</span><span class="sxs-lookup"><span data-stu-id="9508b-256">❌ **DISALLOWED: Changing the value of an attribute that *is* observable**</span></span>

- <span data-ttu-id="9508b-257">❓ **WYMAGA WYROKU: Usunięcie atrybutu**</span><span class="sxs-lookup"><span data-stu-id="9508b-257">❓ **REQUIRES JUDGMENT: Removing an attribute**</span></span>

  <span data-ttu-id="9508b-258">W większości przypadków usunięcie atrybutu <xref:System.NonSerializedAttribute>(na przykład) jest zmianą podziału.</span><span class="sxs-lookup"><span data-stu-id="9508b-258">In most cases, removing an attribute (such as <xref:System.NonSerializedAttribute>) is a breaking change.</span></span>

## <a name="platform-support"></a><span data-ttu-id="9508b-259">Obsługa platform</span><span class="sxs-lookup"><span data-stu-id="9508b-259">Platform support</span></span>

- <span data-ttu-id="9508b-260">✔️ **DOZWOLONE: Obsługa operacji na platformie, która wcześniej nie była obsługiwana**</span><span class="sxs-lookup"><span data-stu-id="9508b-260">✔️ **ALLOWED: Supporting an operation on a platform that was previously not supported**</span></span>

- <span data-ttu-id="9508b-261">❌**NIEDOZWOLONE: Nie obsługuje lub teraz wymaga określonego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**</span><span class="sxs-lookup"><span data-stu-id="9508b-261">❌ **DISALLOWED: Not supporting or now requiring a specific service pack for an operation that was previously supported on a platform**</span></span>

## <a name="internal-implementation-changes"></a><span data-ttu-id="9508b-262">Zmiany w implementacji wewnętrznej</span><span class="sxs-lookup"><span data-stu-id="9508b-262">Internal implementation changes</span></span>

- <span data-ttu-id="9508b-263">❓ **WYMAGA WYROKU: Zmiana powierzchni typu wewnętrznego**</span><span class="sxs-lookup"><span data-stu-id="9508b-263">❓ **REQUIRES JUDGMENT: Changing the surface area of an internal type**</span></span>

   <span data-ttu-id="9508b-264">Takie zmiany są ogólnie dozwolone, chociaż łamią prywatną refleksję.</span><span class="sxs-lookup"><span data-stu-id="9508b-264">Such changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="9508b-265">W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależy od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-265">In some cases, where popular third-party libraries or a large number of developers depend on the internal APIs, such changes may not be allowed.</span></span>

- <span data-ttu-id="9508b-266">❓ **WYMAGA WYROKU: Zmiana wewnętrznego wdrożenia członka**</span><span class="sxs-lookup"><span data-stu-id="9508b-266">❓ **REQUIRES JUDGMENT: Changing the internal implementation of a member**</span></span>

  <span data-ttu-id="9508b-267">Zmiany te są ogólnie dozwolone, chociaż przerywają prywatną refleksję.</span><span class="sxs-lookup"><span data-stu-id="9508b-267">These changes are generally allowed, although they break private reflection.</span></span> <span data-ttu-id="9508b-268">W niektórych przypadkach, gdy kod klienta często zależy od prywatnego odbicia lub gdy zmiana wprowadza niezamierzone skutki uboczne, zmiany te mogą nie być dozwolone.</span><span class="sxs-lookup"><span data-stu-id="9508b-268">In some cases, where customer code frequently depends on private reflection or where the change introduces unintended side effects, these changes may not be allowed.</span></span>

- <span data-ttu-id="9508b-269">✔️ **DOZWOLONE: Poprawa wydajności operacji**</span><span class="sxs-lookup"><span data-stu-id="9508b-269">✔️ **ALLOWED: Improving the performance of an operation**</span></span>

   <span data-ttu-id="9508b-270">Możliwość modyfikowania wydajności operacji jest niezbędna, ale takie zmiany mogą złamać kod, który opiera się na bieżącej szybkości operacji.</span><span class="sxs-lookup"><span data-stu-id="9508b-270">The ability to modify the performance of an operation is essential, but such changes can break code that relies upon the current speed of an operation.</span></span> <span data-ttu-id="9508b-271">Jest to szczególnie prawdziwe w przypadku kodu, który zależy od czasu operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="9508b-271">This is particularly true of code that depends on the timing of asynchronous operations.</span></span> <span data-ttu-id="9508b-272">Zmiana wydajności nie powinna mieć wpływu na inne zachowanie danego interfejsu API; w przeciwnym razie zmiana będzie przełomowa.</span><span class="sxs-lookup"><span data-stu-id="9508b-272">The performance change should have no effect on other behavior of the API in question; otherwise, the change will be breaking.</span></span>

- <span data-ttu-id="9508b-273">✔️ **DOZWOLONE: Pośrednio (i często niekorzystnie) zmiana wykonania operacji**</span><span class="sxs-lookup"><span data-stu-id="9508b-273">✔️ **ALLOWED: Indirectly (and often adversely) changing the performance of an operation**</span></span>

  <span data-ttu-id="9508b-274">Jeśli dany przepis nie jest sklasyfikowany jako łamanie z innego powodu, jest to dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="9508b-274">If the change in question is not categorized as breaking for some other reason, this is acceptable.</span></span> <span data-ttu-id="9508b-275">Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub które dodają nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="9508b-275">Often, actions need to be taken that may include extra operations or that add new functionality.</span></span> <span data-ttu-id="9508b-276">To prawie zawsze wpłynie na wydajność, ale może być niezbędne, aby interfejs API, o których mowa, działał zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9508b-276">This will almost always affect performance but may be essential to make the API in question function as expected.</span></span>

- <span data-ttu-id="9508b-277">❌**NIEDOZWOLONE: Zmiana synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**</span><span class="sxs-lookup"><span data-stu-id="9508b-277">❌ **DISALLOWED: Changing a synchronous API to asynchronous (and vice versa)**</span></span>

## <a name="code-changes"></a><span data-ttu-id="9508b-278">Zmiany kodu</span><span class="sxs-lookup"><span data-stu-id="9508b-278">Code changes</span></span>

- <span data-ttu-id="9508b-279">✔️ **DOZWOLONE: Dodawanie [paramów](../../csharp/language-reference/keywords/params.md) do parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-279">✔️ **ALLOWED: Adding [params](../../csharp/language-reference/keywords/params.md) to a parameter**</span></span>

- <span data-ttu-id="9508b-280">❌**NIEDOZWOLONE: Zmiana [struktury](../../csharp/language-reference/builtin-types/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**</span><span class="sxs-lookup"><span data-stu-id="9508b-280">❌ **DISALLOWED: Changing a [struct](../../csharp/language-reference/builtin-types/struct.md) to a [class](../../csharp/language-reference/keywords/class.md) and vice versa**</span></span>

- <span data-ttu-id="9508b-281">❌**NIEDOZWOLONE: Dodawanie [zaznaczonego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do bloku kodu**</span><span class="sxs-lookup"><span data-stu-id="9508b-281">❌ **DISALLOWED: Adding the [checked](../../csharp/language-reference/keywords/virtual.md) keyword to a code block**</span></span>

   <span data-ttu-id="9508b-282">Ta zmiana może spowodować kod, <xref:System.OverflowException> który wcześniej wykonywane do wyrzucania i jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="9508b-282">This change may cause code that previously executed to throw an <xref:System.OverflowException> and is unacceptable.</span></span>

- <span data-ttu-id="9508b-283">❌**NIEDOZWOLONE: Usuwanie [paramów](../../csharp/language-reference/keywords/params.md) z parametru**</span><span class="sxs-lookup"><span data-stu-id="9508b-283">❌ **DISALLOWED: Removing [params](../../csharp/language-reference/keywords/params.md) from a parameter**</span></span>

- <span data-ttu-id="9508b-284">❌**NIEDOZWOLONE: Zmiana kolejności, w jakiej zdarzenia są uruchamiane**</span><span class="sxs-lookup"><span data-stu-id="9508b-284">❌ **DISALLOWED: Changing the order in which events are fired**</span></span>

  <span data-ttu-id="9508b-285">Deweloperzy mogą rozsądnie oczekiwać, że zdarzenia będą uruchamiane w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9508b-285">Developers can reasonably expect events to fire in the same order, and developer code frequently depends on the order in which events are fired.</span></span>

- <span data-ttu-id="9508b-286">❌**NIEDOZWOLONE: Usuwanie poruszenie zdarzenia w danej akcji**</span><span class="sxs-lookup"><span data-stu-id="9508b-286">❌ **DISALLOWED: Removing the raising of an event on a given action**</span></span>

- <span data-ttu-id="9508b-287">❌**NIEDOZWOLONE: Zmiana liczby podanych zdarzeń jest wywoływana**</span><span class="sxs-lookup"><span data-stu-id="9508b-287">❌ **DISALLOWED: Changing the number of times given events are called**</span></span>

- <span data-ttu-id="9508b-288">❌**NIEDOZWOLONE: Dodawanie <xref:System.FlagsAttribute> do typu wyliczenia**</span><span class="sxs-lookup"><span data-stu-id="9508b-288">❌ **DISALLOWED: Adding the <xref:System.FlagsAttribute> to an enumeration type**</span></span>
