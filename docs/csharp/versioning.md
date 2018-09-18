---
title: C# Versioning — Przewodnik po języku C#
description: Zrozumienie sposobu działania przechowywanie wersji w języku C# i .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 949b7414116169cada62b48392f37809f26d7ff9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970243"
---
# <a name="versioning-in-c"></a><span data-ttu-id="47667-103">Przechowywanie wersji w języku C#</span><span class="sxs-lookup"><span data-stu-id="47667-103">Versioning in C#</span></span> #

<span data-ttu-id="47667-104">W tym samouczku dowiesz się, jakie versioning oznacza, że na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="47667-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="47667-105">Poznasz również czynniki do rozważenia podczas przechowywania wersji biblioteki, a także uaktualnienie do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47667-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="47667-106">Tworzenie bibliotek</span><span class="sxs-lookup"><span data-stu-id="47667-106">Authoring Libraries</span></span>

<span data-ttu-id="47667-107">Jako deweloper, który został utworzony z bibliotekami .NET do użytku publicznego, udało Ci się najbardziej prawdopodobnie zostały w sytuacjach, w którym trzeba wdrożyć nowe aktualizacje.</span><span class="sxs-lookup"><span data-stu-id="47667-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="47667-108">Jak obniżyć o tym procesie ma znaczenie dużo, jak należy się upewnić, że jest bezproblemowe przejście z istniejącego kodu do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47667-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="47667-109">Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:</span><span class="sxs-lookup"><span data-stu-id="47667-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="47667-110">Semantic Versioning</span><span class="sxs-lookup"><span data-stu-id="47667-110">Semantic Versioning</span></span>

<span data-ttu-id="47667-111">[Przechowywanie wersji semantycznej](http://semver.org/) (SemVer w skrócie) jest konwencję nazewnictwa, stosowany do wersji biblioteki oznaczającego punktów kontrolnych określonych zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="47667-111">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="47667-112">Najlepiej, jeśli informacje o wersji, które zapewniają biblioteki powinny pomóc deweloperom Określanie zgodności z projektami, które korzystają z starsze wersje tego takie same biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47667-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="47667-113">Format składnika 3 jest najbardziej podstawowym sposobem SemVer `MAJOR.MINOR.PATCH`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="47667-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

* <span data-ttu-id="47667-114">`MAJOR` jest zwiększany po wprowadzeniu zmian niezgodnych interfejsów API</span><span class="sxs-lookup"><span data-stu-id="47667-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="47667-115">`MINOR` jest zwiększany po dodaniu funkcji w sposób zgodny wstecz</span><span class="sxs-lookup"><span data-stu-id="47667-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="47667-116">`PATCH` jest zwiększany po wprowadzeniu poprawki wstecznie zgodny</span><span class="sxs-lookup"><span data-stu-id="47667-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="47667-117">Istnieją również sposoby, aby określić inne scenariusze, takie jak wersje wstępne itp., stosując informacje o wersji do biblioteki programu .NET.</span><span class="sxs-lookup"><span data-stu-id="47667-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="47667-118">Wstecznej zgodności</span><span class="sxs-lookup"><span data-stu-id="47667-118">Backwards Compatibility</span></span>

<span data-ttu-id="47667-119">Jak zwolnieniu nowe wersje biblioteki wstecznej zgodności z poprzednimi wersjami najprawdopodobniej będzie jedną z głównych problemów.</span><span class="sxs-lookup"><span data-stu-id="47667-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="47667-120">Nową wersję biblioteki jest zgodna z poprzednią wersją kod, który jest zależny od poprzedniej wersji można gdy kompilowany ponownie, pracować z nową wersją źródłowego.</span><span class="sxs-lookup"><span data-stu-id="47667-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="47667-121">Nową wersję biblioteki jest zgodny z binarnego, aplikacja, która była uzależniona od starej wersji bez ponownej kompilacji, pracy z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="47667-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="47667-122">Oto kilka rzeczy, które należy uwzględnić podczas próby utrzymania wstecznej zgodności z poprzednimi wersjami biblioteki:</span><span class="sxs-lookup"><span data-stu-id="47667-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="47667-123">Metody wirtualne: po ustawieniu metodę wirtualną niewirtualną w nowej wersji oznacza, że projekty, które zastępują tej metody do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="47667-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="47667-124">To jest ogromna istotnej zmiany i jest zdecydowanie odradzane.</span><span class="sxs-lookup"><span data-stu-id="47667-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="47667-125">Podpisy metod: podczas aktualizowania zachowanie metody wymaga zmień jej sygnaturę tak dobrze, należy zamiast tego utworzyć przeciążenia tak, aby kod wywoływanie tej metody będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="47667-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="47667-126">Zawsze możesz manipulować stary podpis metody do wywołania w podpisie metody nowy, aby implementacji pozostanie spójna.</span><span class="sxs-lookup"><span data-stu-id="47667-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="47667-127">[Atrybut przestarzałe](programming-guide/concepts/attributes/common-attributes.md#Obsolete): w kodzie można użyć tego atrybutu, aby określić klas lub składowych klasy, które są przestarzałe i może być usunięte w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="47667-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="47667-128">Dzięki temu deweloperzy przy użyciu biblioteki lepiej są przygotowywane na temat przełomowych zmian.</span><span class="sxs-lookup"><span data-stu-id="47667-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="47667-129">Argumenty opcjonalne. metoda: Po wprowadzić obowiązkowe argumenty metody wcześniej opcjonalne lub zmienić ich wartości domyślne, a następnie cały kod, który nie dostarcza tych argumentów należy do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="47667-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="47667-130">Tworzenie obowiązkowe Argumenty opcjonalne powinny mieć bardzo niewielkim stopniu wpływa, zwłaszcza, jeśli go nie zmienia zachowanie metody.</span><span class="sxs-lookup"><span data-stu-id="47667-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="47667-131">Łatwiejsze wprowadzeniu go dla użytkowników uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne, ich uaktualni wcześniej.</span><span class="sxs-lookup"><span data-stu-id="47667-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="47667-132">Plik konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="47667-132">Application Configuration File</span></span>

<span data-ttu-id="47667-133">Jako deweloper platformy .NET, istnieje wysokie prawdopodobieństwo, napotkanych wcześniej [ `app.config` pliku](../framework/configure-apps/file-schema/index.md) obecne w większości typów projektów.</span><span class="sxs-lookup"><span data-stu-id="47667-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="47667-134">Ten plik prostej konfiguracji można długą drogę do poprawy wprowadzania nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="47667-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="47667-135">Ogólnie należy projektować bibliotek w taki sposób, że informacje, która prawdopodobnie się regularnie zmieniane są przechowywane w `app.config` plików dzięki temu po zaktualizowaniu tych informacji w pliku config starszych wersji po prostu musi zostać zastąpiony nowym plikiem bez konieczności ponownej kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47667-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="47667-136">Korzystanie z biblioteki</span><span class="sxs-lookup"><span data-stu-id="47667-136">Consuming Libraries</span></span>

<span data-ttu-id="47667-137">Jako deweloper, który wykorzystuje bibliotek .NET, utworzone przez innych programistów jest najprawdopodobniej pamiętać, że nowa wersja biblioteki może nie być w pełni zgodne z projektem i często może znaleźć się konieczności aktualizowania kodu do pracy z tymi zmianami.</span><span class="sxs-lookup"><span data-stu-id="47667-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="47667-138">Szczęście dla Ciebie języka C# i ekosystemu .NET jest powiązana z funkcji i technik, które pozwalają łatwo aktualizować naszej aplikacji do pracy z nowe wersje bibliotek, które może powodować przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="47667-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="47667-139">Przekierowanie powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="47667-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="47667-140">Możesz użyć `app.config` plik, aby zaktualizować wersję biblioteki używany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="47667-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="47667-141">Dodając tak zwany [ *przekierowanie powiązania* ](../framework/configure-apps/redirect-assembly-versions.md) usługi można użyć nowej wersji biblioteki, bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47667-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="47667-142">W poniższym przykładzie pokazano, jak należy zaktualizować aplikacji `app.config` plik do użycia `1.0.1` wersję poprawki `ReferencedLibrary` zamiast `1.0.0` pierwotnie został skompilowany przy użyciu wersji.</span><span class="sxs-lookup"><span data-stu-id="47667-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="47667-143">Ta metoda będzie działać tylko, jeśli nowa wersja `ReferencedLibrary` jest binarny zgodny z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="47667-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="47667-144">Zobacz [zgodności z poprzednimi wersjami](#backwards-compatibility) Powyższa sekcja zmian do wyszukania podczas określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="47667-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="47667-145">new</span><span class="sxs-lookup"><span data-stu-id="47667-145">new</span></span>

<span data-ttu-id="47667-146">Możesz użyć `new` modyfikator, aby ukryć dziedziczone elementy członkowskie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="47667-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="47667-147">Jest to jeden sposób pochodne mogą odpowiadać na aktualizacje w klasach bazowych.</span><span class="sxs-lookup"><span data-stu-id="47667-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="47667-148">Wykonaj poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="47667-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="47667-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="47667-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="47667-150">W powyższym przykładzie widać, jak `DerivedClass` ukrywa `MyMethod` metoda obecne w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="47667-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="47667-151">Oznacza to, że gdy klasę bazową w nowej wersji biblioteki dodaje element członkowski, który już istnieje w klasie pochodnej, można użyć `new` modyfikator w swojej składowej klasy pochodnej spowoduje ukrycie składowej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="47667-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="47667-152">Gdy nie `new` modyfikator jest określony, klasę pochodną będzie domyślnie Ukryj członków powodujące konflikt w klasie bazowej, mimo że ostrzeżenia kompilatora, który zostanie wygenerowany kod zostanie skompilowany nadal.</span><span class="sxs-lookup"><span data-stu-id="47667-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="47667-153">Oznacza to, że dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowej wersji biblioteki pliku źródłowym, jak i plik binarny jest zgodny z kodem, który zależy od niego.</span><span class="sxs-lookup"><span data-stu-id="47667-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="47667-154">override</span><span class="sxs-lookup"><span data-stu-id="47667-154">override</span></span>

<span data-ttu-id="47667-155">`override` Modyfikator oznacza, że implementacja pochodnej rozszerza implementację składowej klasy bazowej, a nie ukrywa go.</span><span class="sxs-lookup"><span data-stu-id="47667-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="47667-156">Składowej klasy bazowej, musi mieć `virtual` modyfikator stosowane do niego.</span><span class="sxs-lookup"><span data-stu-id="47667-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="47667-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="47667-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="47667-158">`override` Modyfikator jest obliczane w czasie kompilacji i kompilator będzie sygnalizować błąd, jeśli nie znajdzie wirtualna elementu członkowskiego do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="47667-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="47667-159">Swojej wiedzy na temat technik opisano, jak również zrozumieć, jakie sytuacjach, aby umożliwić ich używanie będzie długą drogę do poprawienia łatwości przejścia między wersjami biblioteki.</span><span class="sxs-lookup"><span data-stu-id="47667-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
