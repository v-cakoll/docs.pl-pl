---
title: C# Versioning - Przewodnik języka C#
description: Dowiedz się, jak działa przechowywanie wersji w językach C# i NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dc192337e4eaa5f9f1d6509ea8c15deeac34a48c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645456"
---
# <a name="versioning-in-c"></a><span data-ttu-id="2ec32-103">Przechowywanie wersji w języku C\#</span><span class="sxs-lookup"><span data-stu-id="2ec32-103">Versioning in C\#</span></span>

<span data-ttu-id="2ec32-104">W tym samouczku dowiesz się, co oznacza przechowywanie wersji w .NET.</span><span class="sxs-lookup"><span data-stu-id="2ec32-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="2ec32-105">Poznasz również czynniki, które należy wziąć pod uwagę podczas przechowywania wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2ec32-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="2ec32-106">Tworzenie bibliotek</span><span class="sxs-lookup"><span data-stu-id="2ec32-106">Authoring Libraries</span></span>

<span data-ttu-id="2ec32-107">Jako deweloper, który utworzył biblioteki platformy .NET do użytku publicznego, najprawdopodobniej byłeś w sytuacjach, w których musisz wdrożyć nowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="2ec32-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="2ec32-108">Sposób, w jaki można przejść do tego procesu ma duże znaczenie, jak trzeba, aby upewnić się, że istnieje bezproblemowe przejście istniejącego kodu do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2ec32-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="2ec32-109">Oto kilka rzeczy, które należy wziąć pod uwagę podczas tworzenia nowej wersji:</span><span class="sxs-lookup"><span data-stu-id="2ec32-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="2ec32-110">Przechowywanie wersji semantycznych</span><span class="sxs-lookup"><span data-stu-id="2ec32-110">Semantic Versioning</span></span>

<span data-ttu-id="2ec32-111">[Przechowywanie wersji semantycznych](https://semver.org/) (w skrócie SemVer) to konwencja nazewnictwa stosowana do wersji biblioteki w celu oznaczenia określonych zdarzeń punktu kontrolnego.</span><span class="sxs-lookup"><span data-stu-id="2ec32-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="2ec32-112">W idealnym przypadku informacje o wersji, które podajesz biblioteki powinny pomóc deweloperom określić zgodność z ich projektów, które korzystają ze starszych wersji tej samej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2ec32-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="2ec32-113">Najbardziej podstawowym podejściem do SemVer jest `MAJOR.MINOR.PATCH`format 3-komponentowy, w którym:</span><span class="sxs-lookup"><span data-stu-id="2ec32-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="2ec32-114">`MAJOR`zwiększa się po wprowadzeniu niezgodnych zmian interfejsu API</span><span class="sxs-lookup"><span data-stu-id="2ec32-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="2ec32-115">`MINOR`zwiększa się po dodaniu funkcji w sposób zgodny z do tyłu</span><span class="sxs-lookup"><span data-stu-id="2ec32-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="2ec32-116">`PATCH`jest zwiększany po dokonywalnych wstecznych poprawkach błędów</span><span class="sxs-lookup"><span data-stu-id="2ec32-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="2ec32-117">Istnieją również sposoby, aby określić inne scenariusze, takie jak wersje wstępne itp podczas stosowania informacji o wersji do biblioteki .NET.</span><span class="sxs-lookup"><span data-stu-id="2ec32-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="2ec32-118">Zgodność z przewładem</span><span class="sxs-lookup"><span data-stu-id="2ec32-118">Backwards Compatibility</span></span>

<span data-ttu-id="2ec32-119">Podczas wydawania nowych wersji biblioteki zgodność z poprzednimi wersjami będzie najprawdopodobniej jedną z głównych obaw.</span><span class="sxs-lookup"><span data-stu-id="2ec32-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="2ec32-120">Nowa wersja biblioteki jest źródłem zgodnym z poprzednią wersją, jeśli kod zależny od poprzedniej wersji może, po ponownym skompilacji, pracować z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="2ec32-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span>
<span data-ttu-id="2ec32-121">Nowa wersja biblioteki jest zgodna z binarnym, jeśli aplikacja, która zależała od starej wersji może bez ponownej kompilacji pracować z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="2ec32-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="2ec32-122">Oto kilka rzeczy, które należy wziąć pod uwagę podczas próby zachowania zgodności z powrotem ze starszymi wersjami biblioteki:</span><span class="sxs-lookup"><span data-stu-id="2ec32-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="2ec32-123">Metody wirtualne: Po wprowadzeniu metody wirtualnej niewirtuatu w nowej wersji oznacza to, że projekty, które zastępują tę metodę, będą musiały zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="2ec32-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="2ec32-124">Jest to ogromna zmiana łamiąca i jest zdecydowanie odradzana.</span><span class="sxs-lookup"><span data-stu-id="2ec32-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="2ec32-125">Podpisy metody: Podczas aktualizowania zachowania metody wymaga zmiany jego podpisu, jak również, zamiast tego należy utworzyć przeciążenie, dzięki czemu kod wywołujący do tej metody będzie nadal działać.</span><span class="sxs-lookup"><span data-stu-id="2ec32-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="2ec32-126">Zawsze można manipulować podpis starej metody, aby wywołać do nowego podpisu metody, tak aby implementacja pozostaje spójna.</span><span class="sxs-lookup"><span data-stu-id="2ec32-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="2ec32-127">[Przestarzały atrybut:](language-reference/attributes/general.md#obsolete-attribute)Można użyć tego atrybutu w kodzie, aby określić klasy lub członków klasy, które są przestarzałe i mogą zostać usunięte w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="2ec32-127">[Obsolete attribute](language-reference/attributes/general.md#obsolete-attribute): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="2ec32-128">Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do przełomowych zmian.</span><span class="sxs-lookup"><span data-stu-id="2ec32-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="2ec32-129">Opcjonalne argumenty metody: Po wprowadzeniu wcześniej opcjonalnych argumentów metody obowiązkowe lub zmienić ich wartość domyślną następnie cały kod, który nie dostarcza tych argumentów będą musiały zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="2ec32-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="2ec32-130">Dokonywanie obowiązkowe argumenty opcjonalne powinny mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmienia zachowanie metody.</span><span class="sxs-lookup"><span data-stu-id="2ec32-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="2ec32-131">Im łatwiej będzie użytkownikom uaktualnić do nowej wersji biblioteki, tym większe prawdopodobieństwo, że uaktualnią wcześniej.</span><span class="sxs-lookup"><span data-stu-id="2ec32-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="2ec32-132">Plik konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="2ec32-132">Application Configuration File</span></span>

<span data-ttu-id="2ec32-133">Jako deweloper platformy .NET istnieje bardzo duża szansa, że napotkałeś [ `app.config` plik](../framework/configure-apps/file-schema/index.md) obecny w większości typów projektów.</span><span class="sxs-lookup"><span data-stu-id="2ec32-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="2ec32-134">Ten prosty plik konfiguracyjny może przejść długą drogę do poprawy wdrażania nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="2ec32-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="2ec32-135">Zazwyczaj należy zaprojektować biblioteki w taki sposób, aby informacje, które `app.config` mogą się regularnie zmieniać, były przechowywane w pliku, w ten sposób, gdy takie informacje są aktualizowane, plik konfiguracyjny starszych wersji po prostu musi zostać zastąpiony nowym bez konieczności ponownej kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2ec32-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="2ec32-136">Korzystanie z bibliotek</span><span class="sxs-lookup"><span data-stu-id="2ec32-136">Consuming Libraries</span></span>

<span data-ttu-id="2ec32-137">Jako deweloper, który korzysta z bibliotek platformy .NET utworzonych przez innych deweloperów, najprawdopodobniej zdajesz sobie sprawę, że nowa wersja biblioteki może nie być w pełni zgodna z projektem i często może się okazać, że musisz zaktualizować kod, aby pracować z tymi zmianami.</span><span class="sxs-lookup"><span data-stu-id="2ec32-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="2ec32-138">Na szczęście dla Ciebie, C# i ekosystemu .NET jest wyposażony w funkcje i techniki, które pozwalają nam łatwo zaktualizować naszą aplikację do pracy z nowymi wersjami bibliotek, które mogą wprowadzać przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="2ec32-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="2ec32-139">Przekierowanie powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="2ec32-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="2ec32-140">Za pomocą pliku *app.config* można zaktualizować wersję biblioteki używanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="2ec32-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="2ec32-141">Dodając to, co nazywa się [*przekierowaniem powiązania,*](../framework/configure-apps/redirect-assembly-versions.md)można użyć nowej wersji biblioteki bez konieczności ponownej kompilacji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2ec32-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="2ec32-142">Poniższy przykład pokazuje, jak można zaktualizować plik *app.config* aplikacji, `ReferencedLibrary` aby użyć `1.0.0` wersji `1.0.1` poprawki zamiast wersji, z którą została pierwotnie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="2ec32-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="2ec32-143">Takie podejście będzie działać tylko `ReferencedLibrary` wtedy, gdy nowa wersja jest binarna zgodna z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="2ec32-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="2ec32-144">Zobacz [sekcję Zgodność wsteczna](#backwards-compatibility) powyżej, aby uzyskać zmiany, na które należy zwrócić uwagę podczas określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="2ec32-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="2ec32-145">new</span><span class="sxs-lookup"><span data-stu-id="2ec32-145">new</span></span>

<span data-ttu-id="2ec32-146">`new` Modyfikator służy do ukrywania odziedziczonych elementów członkowskich klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="2ec32-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="2ec32-147">Jest to jeden ze sposobów klas pochodnych może odpowiadać na aktualizacje w klasach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="2ec32-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="2ec32-148">Weźmy następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="2ec32-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="2ec32-149">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="2ec32-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="2ec32-150">Z powyższego przykładu `DerivedClass` można zobaczyć, jak ukrywa metodę obecną `MyMethod` w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="2ec32-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="2ec32-151">Oznacza to, że gdy klasa podstawowa w nowej wersji biblioteki dodaje element członkowski, który `new` już istnieje w klasie pochodnej, można po prostu użyć modyfikatora na element członkowski klasy pochodnej, aby ukryć element członkowski klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="2ec32-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="2ec32-152">Gdy `new` nie określono modyfikatora, klasa pochodna domyślnie ukryje elementy członkowskie powodujące konflikt w klasie podstawowej, chociaż zostanie wygenerowane ostrzeżenie kompilatora, że kod będzie nadal kompilowany.</span><span class="sxs-lookup"><span data-stu-id="2ec32-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="2ec32-153">Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowa wersja biblioteki zarówno źródła i binarne zgodne z kodem, który zależy od niego.</span><span class="sxs-lookup"><span data-stu-id="2ec32-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="2ec32-154">override</span><span class="sxs-lookup"><span data-stu-id="2ec32-154">override</span></span>

<span data-ttu-id="2ec32-155">Modyfikator `override` oznacza implementacji pochodnej rozszerza implementację elementu członkowskiego klasy podstawowej, a nie ukrywa go.</span><span class="sxs-lookup"><span data-stu-id="2ec32-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="2ec32-156">Element członkowski klasy podstawowej musi mieć `virtual` modyfikator stosowane do niego.</span><span class="sxs-lookup"><span data-stu-id="2ec32-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="2ec32-157">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="2ec32-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="2ec32-158">Modyfikator `override` jest oceniany w czasie kompilacji i kompilator zrzuci błąd, jeśli nie znajdzie wirtualnego elementu członkowskiego do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="2ec32-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="2ec32-159">Twoja wiedza na temat omawianych technik i zrozumienie sytuacji, w których można z nich korzystać, będzie przejść długą drogę w kierunku złagodzenia przejścia między wersjami biblioteki.</span><span class="sxs-lookup"><span data-stu-id="2ec32-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
