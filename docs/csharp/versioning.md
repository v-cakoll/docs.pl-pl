---
title: C#Obsługa wersji — C# Przewodnik
description: Informacje o C# działaniu wersji i programie .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: ee123893ac8baa0a55bdf69ce49fb6fcb87601b4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240005"
---
# <a name="versioning-in-c"></a><span data-ttu-id="c445a-103">Przechowywanie wersji w języku C\#</span><span class="sxs-lookup"><span data-stu-id="c445a-103">Versioning in C\#</span></span>

<span data-ttu-id="c445a-104">W tym samouczku dowiesz się, jakie wersje są używane w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="c445a-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="c445a-105">Poznasz również czynniki, które należy wziąć pod uwagę w przypadku przechowywania wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c445a-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="c445a-106">Tworzenie bibliotek</span><span class="sxs-lookup"><span data-stu-id="c445a-106">Authoring Libraries</span></span>

<span data-ttu-id="c445a-107">Jako deweloper, który utworzył biblioteki platformy .NET do użytku publicznego, najprawdopodobniej zachodzi konieczność wdrożenia nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="c445a-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="c445a-108">Sposób działania tego procesu polega na tym, że zachodzi taka potrzeba, aby upewnić się, że istnieje bezproblemowe przejście istniejącego kodu do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c445a-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="c445a-109">Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:</span><span class="sxs-lookup"><span data-stu-id="c445a-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="c445a-110">Wersja semantyczna</span><span class="sxs-lookup"><span data-stu-id="c445a-110">Semantic Versioning</span></span>

<span data-ttu-id="c445a-111">[Wersja semantyczna](https://semver.org/) (SemVer for Short) to Konwencja nazewnictwa stosowana do wersji biblioteki do oznaczania określonych zdarzeń punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="c445a-111">[Semantic versioning](https://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="c445a-112">W idealnym przypadku informacje o wersji, którą udostępnia Twoja biblioteka, powinny pomóc deweloperom w ustaleniu zgodności z projektami, które korzystają ze starszych wersji tej samej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c445a-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="c445a-113">Najbardziej podstawowym podejściem do SemVer jest format 3 składników `MAJOR.MINOR.PATCH`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="c445a-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>

- <span data-ttu-id="c445a-114">`MAJOR` jest zwiększana w przypadku wprowadzania niezgodnych zmian interfejsu API</span><span class="sxs-lookup"><span data-stu-id="c445a-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
- <span data-ttu-id="c445a-115">`MINOR` zwiększa się w przypadku dodawania funkcji w sposób zgodny z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="c445a-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
- <span data-ttu-id="c445a-116">`PATCH` jest zwiększana w przypadku wprowadzania poprawek błędów zgodnych z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="c445a-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="c445a-117">Istnieją również sposoby określania innych scenariuszy, takich jak wersje wstępne itp. w przypadku stosowania informacji o wersji do biblioteki platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c445a-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="c445a-118">Zgodność z poprzednimi wersjami</span><span class="sxs-lookup"><span data-stu-id="c445a-118">Backwards Compatibility</span></span>

<span data-ttu-id="c445a-119">Po udostępnieniu nowych wersji biblioteki, zgodność z poprzednimi wersjami będzie prawdopodobnie jednym z najważniejszych problemów.</span><span class="sxs-lookup"><span data-stu-id="c445a-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="c445a-120">Nowa wersja biblioteki jest zgodna ze źródłem w poprzedniej wersji, jeśli kod, który zależy od poprzedniej wersji, może, po ponownym skompilowaniu, współpracować z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="c445a-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="c445a-121">Nowa wersja biblioteki jest zgodna z binarną, jeśli aplikacja, która jest zależna od starej wersji, może, bez ponownej kompilacji, działała z nową wersją.</span><span class="sxs-lookup"><span data-stu-id="c445a-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="c445a-122">Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas próby utrzymania zgodności z poprzednimi wersjami w przypadku starszych wersji biblioteki:</span><span class="sxs-lookup"><span data-stu-id="c445a-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

- <span data-ttu-id="c445a-123">Metody wirtualne: w przypadku wybrania w nowej wersji metody wirtualnej, która nie jest wirtualna, oznacza to, że projekty, które przesłaniają tę metodę, będą musiały zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="c445a-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="c445a-124">Jest to ogromna istotna zmiana i zdecydowanie odradza się.</span><span class="sxs-lookup"><span data-stu-id="c445a-124">This is a huge breaking change and is strongly discouraged.</span></span>
- <span data-ttu-id="c445a-125">Sygnatury metod: w przypadku aktualizowania zachowania metody wymaga również zmiany jego podpisu, dlatego należy utworzyć Przeciążenie, aby kod wywołujący do tej metody nadal działał.</span><span class="sxs-lookup"><span data-stu-id="c445a-125">Method signatures: When updating a method behavior requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="c445a-126">Zawsze możesz manipulować starym podpisem metody, aby wywołać nową metodę sygnatury, tak aby implementacja była spójna.</span><span class="sxs-lookup"><span data-stu-id="c445a-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
- <span data-ttu-id="c445a-127">[Przestarzały atrybut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): można użyć tego atrybutu w kodzie, aby określić klasy lub członków klasy, które są przestarzałe i które mogą zostać usunięte w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="c445a-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span> <span data-ttu-id="c445a-128">Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do istotnych zmian.</span><span class="sxs-lookup"><span data-stu-id="c445a-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
- <span data-ttu-id="c445a-129">Argumenty metody opcjonalnej: po wprowadzeniu poprzednio opcjonalne argumenty metody obowiązkowo lub zmiany wartości domyślnej, cały kod, który nie dostarcza tych argumentów, będzie musiał zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="c445a-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>

> [!NOTE]
> <span data-ttu-id="c445a-130">Obowiązkowe argumenty opcjonalne powinny mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmieni zachowanie metody.</span><span class="sxs-lookup"><span data-stu-id="c445a-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behavior.</span></span>

<span data-ttu-id="c445a-131">Dzięki temu użytkownicy będą mogli uaktualnić do nowej wersji biblioteki, im większa jest możliwość ich uaktualnienia.</span><span class="sxs-lookup"><span data-stu-id="c445a-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="c445a-132">Plik konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="c445a-132">Application Configuration File</span></span>

<span data-ttu-id="c445a-133">Deweloperem platformy .NET jest bardzo wysoka szansa [, że plik `app.config`](../framework/configure-apps/file-schema/index.md) występuje w większości typów projektów.</span><span class="sxs-lookup"><span data-stu-id="c445a-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](../framework/configure-apps/file-schema/index.md) present in most project types.</span></span>
<span data-ttu-id="c445a-134">Ten prosty plik konfiguracji może być długim sposobem ulepszania wdrażania nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="c445a-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="c445a-135">Zazwyczaj należy zaprojektować biblioteki w taki sposób, że informacje, które prawdopodobnie zmieniają się regularnie, są przechowywane w pliku `app.config`, w ten sposób, gdy takie informacje zostaną zaktualizowane, plik konfiguracyjny starszych wersji musi zostać zastąpiony nowym, bez konieczności ponownej kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c445a-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated, the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="c445a-136">Używanie bibliotek</span><span class="sxs-lookup"><span data-stu-id="c445a-136">Consuming Libraries</span></span>

<span data-ttu-id="c445a-137">Deweloperzy korzystający z bibliotek .NET zbudowanych przez innych deweloperów najprawdopodobniej wiedzą, że nowa wersja biblioteki może nie być w pełni zgodna z projektem i często można sprawdzić, czy trzeba zaktualizować swój kod, aby pracować z tymi zmianami.</span><span class="sxs-lookup"><span data-stu-id="c445a-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="c445a-138">Cieszymy dla Ciebie, C# a ekosystem .NET obejmuje funkcje i techniki, które umożliwiają łatwe aktualizowanie naszej aplikacji do pracy z nowymi wersjami bibliotek, które mogą spowodować istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="c445a-138">Lucky for you, C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="c445a-139">Przekierowanie powiązania zestawu</span><span class="sxs-lookup"><span data-stu-id="c445a-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="c445a-140">Plik *App. config* służy do aktualizowania wersji biblioteki używanej przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="c445a-140">You can use the *app.config* file to update the version of a library your app uses.</span></span> <span data-ttu-id="c445a-141">Dodając jak nazywa się [*przekierowanie powiązania*](../framework/configure-apps/redirect-assembly-versions.md), możesz użyć nowej wersji biblioteki bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c445a-141">By adding what is called a [*binding redirect*](../framework/configure-apps/redirect-assembly-versions.md), you can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="c445a-142">W poniższym przykładzie pokazano, jak zaktualizować plik *App. config* aplikacji, tak aby używał `1.0.1` wersji poprawki `ReferencedLibrary` zamiast `1.0.0` wersji, w której został on pierwotnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="c445a-142">The following example shows how you would update your app's *app.config* file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="c445a-143">Ta metoda będzie działała tylko wtedy, gdy nowa wersja `ReferencedLibrary` jest binarna zgodna z Twoją aplikacją.</span><span class="sxs-lookup"><span data-stu-id="c445a-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="c445a-144">W sekcji [zgodność z poprzednimi wersjami](#backwards-compatibility) powyżej znajdziesz zmiany, które należy wyszukać podczas określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="c445a-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="c445a-145">new</span><span class="sxs-lookup"><span data-stu-id="c445a-145">new</span></span>

<span data-ttu-id="c445a-146">Używasz modyfikatora `new`, aby ukryć dziedziczone elementy członkowskie klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c445a-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="c445a-147">Jest to jeden ze sposobów, w jaki klasy pochodne mogą odpowiadać na aktualizacje w klasach bazowych.</span><span class="sxs-lookup"><span data-stu-id="c445a-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="c445a-148">Wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c445a-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="c445a-149">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="c445a-149">**Output**</span></span>

```console
A base method
A derived method
```

<span data-ttu-id="c445a-150">Z powyższego przykładu można zobaczyć, jak `DerivedClass` ukrywa metodę `MyMethod` obecną w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="c445a-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="c445a-151">Oznacza to, że gdy klasa bazowa w nowej wersji biblioteki dodaje element członkowski, który już istnieje w klasie pochodnej, można po prostu użyć modyfikatora `new` w składowej klasy pochodnej, aby ukryć element członkowski klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="c445a-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="c445a-152">Gdy nie jest określony modyfikator `new`, Klasa pochodna domyślnie ukrywa elementy członkowskie powodujące konflikt w klasie bazowej, mimo że zostanie wygenerowane Ostrzeżenie kompilatora, kod nadal zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="c445a-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="c445a-153">Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy powoduje, że nowa wersja biblioteki jest zgodna z kodem, który od niego zależy.</span><span class="sxs-lookup"><span data-stu-id="c445a-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="c445a-154">zastąpienie</span><span class="sxs-lookup"><span data-stu-id="c445a-154">override</span></span>

<span data-ttu-id="c445a-155">Modyfikator `override` oznacza, że implementacja pochodna rozszerza implementację składowej klasy bazowej, a nie ukrywa ją.</span><span class="sxs-lookup"><span data-stu-id="c445a-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="c445a-156">Element członkowski klasy bazowej musi mieć zastosowany modyfikator `virtual`.</span><span class="sxs-lookup"><span data-stu-id="c445a-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="c445a-157">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="c445a-157">**Output**</span></span>

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="c445a-158">Modyfikator `override` jest oceniany w czasie kompilacji, a kompilator zgłosi błąd, jeśli nie znajdzie wirtualnego elementu członkowskiego do przesłonięcia.</span><span class="sxs-lookup"><span data-stu-id="c445a-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="c445a-159">Wiedza o omawianych technikach i zrozumieniu sytuacji, w których można z nich korzystać, będzie mieć na celu szybkie przechodzenie między wersjami biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c445a-159">Your knowledge of the discussed techniques and your understanding of the situations in which to use them, will go a long way towards easing the transition between versions of a library.</span></span>
