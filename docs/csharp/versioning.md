---
title: Przechowywanie wersji języka C# — przewodnik po języku C#
description: Dowiedz się, jak działa przechowywanie wersji w językach C# i .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156470"
---
# <a name="versioning-in-c"></a><span data-ttu-id="914f6-103">Przechowywanie wersji w C\#</span><span class="sxs-lookup"><span data-stu-id="914f6-103">Versioning in C\#</span></span>

<span data-ttu-id="914f6-104">W tym samouczku dowiesz się, co oznacza przechowywanie wersji w .NET.</span><span class="sxs-lookup"><span data-stu-id="914f6-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="914f6-105">Dowiesz się również, które należy wziąć pod uwagę podczas wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="914f6-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="914f6-106">Biblioteki tworzenia</span><span class="sxs-lookup"><span data-stu-id="914f6-106">Authoring Libraries</span></span>

<span data-ttu-id="914f6-107">Jako deweloper, który utworzył biblioteki .NET do użytku publicznego, najprawdopodobniej byłeś w sytuacjach, w których musisz wdrożyć nowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="914f6-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="914f6-108">Sposób, w jaki przechodzisz do tego procesu, ma duże znaczenie, ponieważ musisz upewnić się, że istnieje płynne przejście istniejącego kodu do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="914f6-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="914f6-109">Oto kilka rzeczy, które należy wziąć pod uwagę podczas tworzenia nowej wersji:</span><span class="sxs-lookup"><span data-stu-id="914f6-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="914f6-110">Przechowywanie wersji semantycznych</span><span class="sxs-lookup"><span data-stu-id="914f6-110">Semantic Versioning</span></span>

<span data-ttu-id="914f6-111">[Przechowywanie wersji semantycznych](https://semver.org/) (semver w skrócie) jest konwencją nazewnictwa stosowaną do wersji biblioteki w celu oznaczania określonych zdarzeń punktu kontrolnego.</span><span class="sxs-lookup"><span data-stu-id="914f6-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="914f6-112">W idealnym przypadku informacje o wersji, które podajesz biblioteki powinny pomóc deweloperom określić zgodność z ich projektów, które korzystają ze starszych wersji tej samej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="914f6-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="914f6-113">Najbardziej podstawowym podejściem do SemVer `MAJOR.MINOR.PATCH`jest format komponentu 3, gdzie:</span><span class="sxs-lookup"><span data-stu-id="914f6-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="914f6-114">`MAJOR`jest zwiększana po wprowadzeniu niezgodnych zmian interfejsu API</span><span class="sxs-lookup"><span data-stu-id="914f6-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="914f6-115">`MINOR`jest zwiększana po dodaniu funkcji w sposób zgodny z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="914f6-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="914f6-116">`PATCH`jest zwiększana po wprowadzeniu poprawek błędów zgodnych z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="914f6-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="914f6-117">Istnieją również sposoby określania innych scenariuszy, takich jak wersje wstępne itp.</span><span class="sxs-lookup"><span data-stu-id="914f6-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="914f6-118">Zgodność z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="914f6-118">Backwards Compatibility</span></span>

<span data-ttu-id="914f6-119">Wraz z wydaniem nowych wersji biblioteki, wsteczna kompatybilność z poprzednimi wersjami będzie najprawdopodobniej jednym z głównych problemów.</span><span class="sxs-lookup"><span data-stu-id="914f6-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="914f6-120">Nowa wersja biblioteki jest potomna zgodna z poprzednią wersją, jeśli kod, który zależy od poprzedniej wersji, może, po ponownym skompilowaniu, pracować z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="914f6-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span>
<span data-ttu-id="914f6-121">Nowa wersja biblioteki jest zgodna z plikami binarnymi, jeśli aplikacja, która zależała od starej wersji, może bez ponownej kompilacji pracować z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="914f6-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="914f6-122">Oto kilka rzeczy, które należy wziąć pod uwagę podczas próby zachowania zgodności wstecznej ze starszymi wersjami biblioteki:</span><span class="sxs-lookup"><span data-stu-id="914f6-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="914f6-123">Metody wirtualne: Po uczynieniu metody wirtualnej niewirtualnej w nowej wersji oznacza to, że projekty, które zastępują tę metodę, będą musiały zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="914f6-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="914f6-124">Jest to ogromna przełomowa zmiana i zdecydowanie odradza się.</span><span class="sxs-lookup"><span data-stu-id="914f6-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="914f6-125">Podpisy metody: Podczas aktualizowania zachowanie metody wymaga zmiany jego podpis, jak również, należy zamiast tego utworzyć przeciążenie, tak aby wywołanie kodu do tej metody będzie nadal działać.</span><span class="sxs-lookup"><span data-stu-id="914f6-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="914f6-126">Zawsze można manipulować podpis starej metody, aby wywołać podpis nowej metody, dzięki czemu implementacja pozostaje spójna.</span><span class="sxs-lookup"><span data-stu-id="914f6-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="914f6-127">[Atrybut Przestarzały](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Można użyć tego atrybutu w kodzie, aby określić klasy lub elementy członkowskie klasy, które są przestarzałe i prawdopodobnie zostaną usunięte w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="914f6-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="914f6-128">Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do przełomowych zmian.</span><span class="sxs-lookup"><span data-stu-id="914f6-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="914f6-129">Opcjonalne argumenty metody: Po wprowadzeniu wcześniej opcjonalnych argumentów metody obowiązkowe lub zmienić ich wartość domyślną, a następnie cały kod, który nie dostarcza tych argumentów będą musiały zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="914f6-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="914f6-130">Wprowadzenie obowiązkowych argumentów opcjonalne powinno mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmienia zachowania metody.</span><span class="sxs-lookup"><span data-stu-id="914f6-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="914f6-131">Im łatwiej będzie użytkownikom uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne jest, że zostaną uaktualnieni wcześniej.</span><span class="sxs-lookup"><span data-stu-id="914f6-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="914f6-132">Plik konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="914f6-132">Application Configuration File</span></span>

<span data-ttu-id="914f6-133">Jako programista .NET istnieje bardzo duża szansa, że napotkałeś [ `app.config` plik](../framework/configure-apps/file-schema/index.md) obecny w większości typów projektów.</span><span class="sxs-lookup"><span data-stu-id="914f6-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="914f6-134">Ten prosty plik konfiguracyjny może przejść długą drogę do poprawy wdrażania nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="914f6-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="914f6-135">Zazwyczaj należy zaprojektować biblioteki w taki sposób, aby informacje, które mogą `app.config` się regularnie zmieniać, były przechowywane w pliku, w ten sposób, gdy takie informacje są aktualizowane, plik konfiguracyjny starszych wersji po prostu musi zostać zastąpiony nową bez konieczności ponownej kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="914f6-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="914f6-136">Korzystanie z bibliotek</span><span class="sxs-lookup"><span data-stu-id="914f6-136">Consuming Libraries</span></span>

<span data-ttu-id="914f6-137">Jako deweloper, który zużywa biblioteki .NET utworzone przez innych deweloperów najprawdopodobniej wiesz, że nowa wersja biblioteki może nie być w pełni zgodne z projektem i często może się okazać, że musisz zaktualizować kod, aby pracować z tymi zmianami.</span><span class="sxs-lookup"><span data-stu-id="914f6-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="914f6-138">Na szczęście dla Ciebie, C# i ekosystemu .NET pochodzi z funkcji i technik, które pozwalają nam łatwo zaktualizować naszą aplikację do pracy z nowymi wersjami bibliotek, które mogą wprowadzać przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="914f6-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="914f6-139">Przekierowanie wiązania złożenia</span><span class="sxs-lookup"><span data-stu-id="914f6-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="914f6-140">Za pomocą pliku *app.config* można zaktualizować wersję biblioteki używanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="914f6-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="914f6-141">Dodając tak zwane [*przekierowanie powiązania,*](../framework/configure-apps/redirect-assembly-versions.md)można użyć nowej wersji biblioteki bez konieczności ponownej kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="914f6-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="914f6-142">W poniższym przykładzie pokazano, jak zaktualizować plik *app.config* `ReferencedLibrary` aplikacji, `1.0.0` aby użyć wersji `1.0.1` poprawki zamiast wersji, z którą został pierwotnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="914f6-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="914f6-143">Takie podejście będzie działać tylko `ReferencedLibrary` wtedy, gdy nowa wersja jest zgodna z plikami binarnymi z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="914f6-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="914f6-144">Zobacz [wstecznej zgodności](#backwards-compatibility) sekcji powyżej zmian, na które należy zwrócić uwagę podczas określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="914f6-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="914f6-145">new</span><span class="sxs-lookup"><span data-stu-id="914f6-145">new</span></span>

<span data-ttu-id="914f6-146">Modyfikator służy `new` do ukrywania dziedziczonych członków klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="914f6-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="914f6-147">Jest to jeden ze sposobów pochodnych klas można odpowiedzieć na aktualizacje w klasach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="914f6-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="914f6-148">Weźmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="914f6-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="914f6-149">**Wyjście**</span><span class="sxs-lookup"><span data-stu-id="914f6-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="914f6-150">W powyższym przykładzie można `DerivedClass` zobaczyć, `MyMethod` jak `BaseClass`ukrywa metodę obecną w pliku .</span><span class="sxs-lookup"><span data-stu-id="914f6-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="914f6-151">Oznacza to, że gdy klasa podstawowa w nowej wersji biblioteki dodaje element członkowski, `new` który już istnieje w klasie pochodnej, można po prostu użyć modyfikatora na element członkowski klasy pochodnej, aby ukryć element członkowski klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="914f6-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="914f6-152">Po `new` nie modyfikator jest określony, klasa pochodna domyślnie ukryć elementy członkowskie powodujące konflikt w klasie podstawowej, mimo że ostrzeżenie kompilatora zostanie wygenerowany kod będzie nadal kompilować.</span><span class="sxs-lookup"><span data-stu-id="914f6-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="914f6-153">Oznacza to, że po prostu dodawanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowa wersja biblioteki zarówno źródło, jak i binarny zgodny z kodem, który zależy od niego.</span><span class="sxs-lookup"><span data-stu-id="914f6-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="914f6-154">override</span><span class="sxs-lookup"><span data-stu-id="914f6-154">override</span></span>

<span data-ttu-id="914f6-155">Modyfikator `override` oznacza implementacji pochodnej rozszerza implementację elementu członkowskiego klasy podstawowej, a nie ukrywa go.</span><span class="sxs-lookup"><span data-stu-id="914f6-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="914f6-156">Element członkowski klasy `virtual` podstawowej musi mieć modyfikator zastosowany do niego.</span><span class="sxs-lookup"><span data-stu-id="914f6-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="914f6-157">**Wyjście**</span><span class="sxs-lookup"><span data-stu-id="914f6-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="914f6-158">Modyfikator `override` jest oceniany w czasie kompilacji i kompilator będzie zgłaszać błąd, jeśli nie znajdzie członka wirtualnego do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="914f6-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="914f6-159">Twoja wiedza na temat omawianych technik i zrozumienie sytuacji, w których można z nich korzystać, będzie przejść długą drogę w kierunku złagodzenia przejścia między wersjami biblioteki.</span><span class="sxs-lookup"><span data-stu-id="914f6-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
