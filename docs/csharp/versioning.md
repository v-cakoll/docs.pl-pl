---
title: C# Versioning — przewodnik C#
description: Zrozumieć sposób działania kontroli wersji w języku C# i .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 4dc8e7e521bf209d6ca69a84534d277fb8a93ea8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351787"
---
# <a name="versioning-in-c"></a><span data-ttu-id="9cc49-103">Przechowywanie wersji w języku C#</span><span class="sxs-lookup"><span data-stu-id="9cc49-103">Versioning in C#</span></span> #

<span data-ttu-id="9cc49-104">W tym samouczku nauczysz się, jakie versioning oznacza, że w środowisku .NET.</span><span class="sxs-lookup"><span data-stu-id="9cc49-104">In this tutorial you'll learn what versioning means in .NET.</span></span> <span data-ttu-id="9cc49-105">Dowiesz się czynniki do rozważenia podczas przechowywania wersji biblioteki, a także uaktualnienie do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cc49-105">You'll also learn the factors to consider when versioning your library as well as upgrading to a new version of the a library.</span></span>

## <a name="authoring-libraries"></a><span data-ttu-id="9cc49-106">Tworzenie bibliotek</span><span class="sxs-lookup"><span data-stu-id="9cc49-106">Authoring Libraries</span></span>

<span data-ttu-id="9cc49-107">Deweloperzy tworzący bibliotek .NET do użytku publicznego udało Ci się najbardziej prawdopodobnie zostały w sytuacjach, w których konieczne wdrażanie nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="9cc49-107">As a developer who has created .NET libraries for public use, you've most likely been in situations where you have to roll out new updates.</span></span> <span data-ttu-id="9cc49-108">Jak przejść na ten tego procesu ma znaczenie dużo, jak należy się upewnić, że jest płynne przejście z istniejącego kodu do nowej wersji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cc49-108">How you go about this process matters a lot as you need to ensure that there's a seamless transition of existing code to the new version of your library.</span></span> <span data-ttu-id="9cc49-109">Oto kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:</span><span class="sxs-lookup"><span data-stu-id="9cc49-109">Here are several things to consider when creating a new release:</span></span>

### <a name="semantic-versioning"></a><span data-ttu-id="9cc49-110">Wersjonowania semantycznego</span><span class="sxs-lookup"><span data-stu-id="9cc49-110">Semantic Versioning</span></span>

<span data-ttu-id="9cc49-111">[Wersjonowania semantycznego](http://semver.org/) (programu SemVer skrócie) jest Konwencja nazewnictwa stosowana do wersji biblioteki oznaczającego zdarzenia określonego punktu kontrolnego.</span><span class="sxs-lookup"><span data-stu-id="9cc49-111">[Semantic versioning](http://semver.org/) (SemVer for short) is a naming convention applied to versions of your library to signify specific milestone events.</span></span>
<span data-ttu-id="9cc49-112">Najlepiej, jeśli informacje o wersji, nadaj biblioteki powinny pomóc deweloperom określania zgodności z projektami korzystające z starsze wersje tego same biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cc49-112">Ideally, the version information you give your library should help developers determine the compatibility with their projects that make use of older versions of that same library.</span></span>

<span data-ttu-id="9cc49-113">Najprostsze podejście do programu SemVer jest w formacie 3 składnika `MAJOR.MINOR.PATCH`, gdzie:</span><span class="sxs-lookup"><span data-stu-id="9cc49-113">The most basic approach to SemVer is the 3 component format `MAJOR.MINOR.PATCH`, where:</span></span>
 
* <span data-ttu-id="9cc49-114">`MAJOR` jest zwiększany po wprowadzeniu zmian interfejsu API niezgodne</span><span class="sxs-lookup"><span data-stu-id="9cc49-114">`MAJOR` is incremented when you make incompatible API changes</span></span>
* <span data-ttu-id="9cc49-115">`MINOR` jest zwiększany po dodaniu funkcji w sposób zgodny wstecz</span><span class="sxs-lookup"><span data-stu-id="9cc49-115">`MINOR` is incremented when you add functionality in a backwards-compatible manner</span></span>
* <span data-ttu-id="9cc49-116">`PATCH` jest zwiększany po wprowadzeniu wstecznie zgodna poprawki błędów</span><span class="sxs-lookup"><span data-stu-id="9cc49-116">`PATCH` is incremented when you make backwards-compatible bug fixes</span></span>

<span data-ttu-id="9cc49-117">Istnieją również sposobów, aby określić inne scenariusze, takie jak wersje wstępne itp., stosując informacje o wersji do biblioteki programu .NET.</span><span class="sxs-lookup"><span data-stu-id="9cc49-117">There are also ways to specify other scenarios like pre-release versions etc. when applying version information to your .NET library.</span></span>

### <a name="backwards-compatibility"></a><span data-ttu-id="9cc49-118">Zapewnienia zgodności</span><span class="sxs-lookup"><span data-stu-id="9cc49-118">Backwards Compatibility</span></span>

<span data-ttu-id="9cc49-119">Jak zwolnić nowych wersji biblioteki, Wstecz zgodność z poprzednimi wersjami najprawdopodobniej będzie jedną z głównych problemów.</span><span class="sxs-lookup"><span data-stu-id="9cc49-119">As you release new versions of your library, backwards compatibility with previous versions will most likely be one of your major concerns.</span></span>
<span data-ttu-id="9cc49-120">Nowa wersja biblioteki jest zgodny z poprzedniej wersji kodu, który jest zależny od poprzedniej wersji gdy ponownie skompilowana, pracy z nową wersję źródła.</span><span class="sxs-lookup"><span data-stu-id="9cc49-120">A new version of your library is source compatible with a previous version if code that depends on the previous version can, when recompiled, work with the new version.</span></span> <span data-ttu-id="9cc49-121">Nowa wersja biblioteki jest zgodny z binarnego, jeśli aplikację, która była uzależniona od starej wersji bez ponownej kompilacji, pracować z nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="9cc49-121">A new version of your library is binary compatible if an application that depended on the old version can, without recompilation, work with the new version.</span></span>

<span data-ttu-id="9cc49-122">Poniżej przedstawiono niektóre czynności, które należy uwzględnić podczas próby Obsługa zapewnienia zgodności z poprzednimi wersjami biblioteki:</span><span class="sxs-lookup"><span data-stu-id="9cc49-122">Here are some things to consider when trying to maintain backwards compatibility with older versions of your library:</span></span>

* <span data-ttu-id="9cc49-123">Metody wirtualne: podczas wprowadzania metody wirtualnej Niewirtualny w nowej wersji oznacza to, że projekty, które zastępują tej metody do zaktualizowania.</span><span class="sxs-lookup"><span data-stu-id="9cc49-123">Virtual methods: When you make a virtual method non-virtual in your new version it means that projects that override that method will have to be updated.</span></span> <span data-ttu-id="9cc49-124">To jest duży istotnej zmiany i jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="9cc49-124">This is a huge breaking change and is strongly discouraged.</span></span>
* <span data-ttu-id="9cc49-125">Metoda podpisów: Jeśli aktualizowanie zachowania — metoda wymaga zmiany jego sygnatura również, należy zamiast tego utworzyć przeciążenia tak, aby kod wywoływanie metody będą nadal działać.</span><span class="sxs-lookup"><span data-stu-id="9cc49-125">Method signatures: When updating a method behaviour requires you to change its signature as well, you should instead create an overload so that code calling into that method will still work.</span></span>
<span data-ttu-id="9cc49-126">Zawsze można manipulować starego podpis metody do wywołania do nowego podpisu metody, aby implementacji pozostaje spójna.</span><span class="sxs-lookup"><span data-stu-id="9cc49-126">You can always manipulate the old method signature to call into the new method signature so that implementation remains consistent.</span></span>
* <span data-ttu-id="9cc49-127">[Atrybut przestarzałe](programming-guide/concepts/attributes/common-attributes.md#Obsolete): w kodzie można użyć tego atrybutu, aby określić klasy lub elementów członkowskich klasy, które zostały uznane za przestarzałe i może być usunięte w przyszłych wersjach.</span><span class="sxs-lookup"><span data-stu-id="9cc49-127">[Obsolete attribute](programming-guide/concepts/attributes/common-attributes.md#Obsolete): You can use this attribute in your code to specify classes or class members that are deprecated and likely to be removed in future versions.</span></span>
<span data-ttu-id="9cc49-128">Dzięki temu deweloperzy przy użyciu biblioteki są lepiej przygotowane pod kątem fundamentalne zmiany.</span><span class="sxs-lookup"><span data-stu-id="9cc49-128">This ensures developers utilizing your library are better prepared for breaking changes.</span></span>
* <span data-ttu-id="9cc49-129">Argumenty opcjonalne metody: Podczas wprowadzania metody wcześniej opcjonalne argumenty obowiązkowe lub zmienić ich wartości domyślne, a następnie całego kodu, który nie dostarcza tych argumentów będzie muszą zostać zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="9cc49-129">Optional Method Arguments: When you make previously optional method arguments compulsory or change their default value then all code that does not supply those arguments will need to be updated.</span></span>
> [!NOTE]
> <span data-ttu-id="9cc49-130">Tworzenie obowiązkowego Argumenty opcjonalne powinien mieć bardzo mały wpływ, zwłaszcza, jeśli nie zmienia zachowanie metody.</span><span class="sxs-lookup"><span data-stu-id="9cc49-130">Making compulsory arguments optional should have very little effect especially if it doesn't change the method's behaviour.</span></span>

<span data-ttu-id="9cc49-131">Łatwiej można ustawić dla użytkowników, aby uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne one uaktualni wcześniej.</span><span class="sxs-lookup"><span data-stu-id="9cc49-131">The easier you make it for your users to upgrade to the new version of your library, the more likely that they will upgrade sooner.</span></span>

### <a name="application-configuration-file"></a><span data-ttu-id="9cc49-132">Plik konfiguracji aplikacji</span><span class="sxs-lookup"><span data-stu-id="9cc49-132">Application Configuration File</span></span>

<span data-ttu-id="9cc49-133">Projektant .NET istnieje bardzo duże ryzyko został napotkany [ `app.config` pliku](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) w większości typów projektów.</span><span class="sxs-lookup"><span data-stu-id="9cc49-133">As a .NET developer there's a very high chance you've encountered [the `app.config` file](https://msdn.microsoft.com/library/1fk1t1t0(v=vs.110).aspx) present in most project types.</span></span>
<span data-ttu-id="9cc49-134">Ten plik prostą konfigurację można zdecydowanie do poprawy wdrażanie nowych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="9cc49-134">This simple configuration file can go a long way into improving the rollout of new updates.</span></span> <span data-ttu-id="9cc49-135">Ogólnie należy projektować w bibliotekach w taki sposób, że mogą się zmieniać regularnie informacje są przechowywane w `app.config` pliku w ten sposób po zaktualizowaniu tych informacji w pliku config starszych wersji musi być zastąpiony nowym bez konieczności ponownej kompilacji biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cc49-135">You should generally design your libraries in such a way that information that is likely to change regularly is stored in the `app.config` file, this way when such information is updated the config file of older versions just needs to be replaced with the new one without the need for recompilation of the library.</span></span>

## <a name="consuming-libraries"></a><span data-ttu-id="9cc49-136">Korzystanie z biblioteki</span><span class="sxs-lookup"><span data-stu-id="9cc49-136">Consuming Libraries</span></span>

<span data-ttu-id="9cc49-137">Deweloper, który wykorzystuje utworzony przez innych bibliotek .NET jest najprawdopodobniej pamiętać, że nowa wersja biblioteki nie może być całkowicie zgodne z projektem i często może okaże się, że konieczności zaktualizuj kod do pracy z tymi zmianami.</span><span class="sxs-lookup"><span data-stu-id="9cc49-137">As a developer that consumes .NET libraries built by other developers you're most likely aware that a new version of a library might not be fully compatible with your project and you might often find yourself having to update your code to work with those changes.</span></span>

<span data-ttu-id="9cc49-138">Szczęście dla Ciebie C# i ekosystemem .NET zawiera funkcje i techniki, które umożliwiają łatwe aktualizacji aplikacji do pracy z nowe wersje bibliotek, które może powodować istotne zmiany.</span><span class="sxs-lookup"><span data-stu-id="9cc49-138">Lucky for you C# and the .NET ecosystem comes with features and techniques that allow us to easily update our app to work with new versions of libraries that might introduce breaking changes.</span></span>

### <a name="assembly-binding-redirection"></a><span data-ttu-id="9cc49-139">Przekierowanie powiązań zestawów</span><span class="sxs-lookup"><span data-stu-id="9cc49-139">Assembly Binding Redirection</span></span>

<span data-ttu-id="9cc49-140">Można użyć `app.config` plik, aby zaktualizować wersję biblioteki używany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="9cc49-140">You can use the `app.config` file to update the version of a library your app uses.</span></span> <span data-ttu-id="9cc49-141">Dodając tak zwany [ *przekierowania powiązania* ](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) Twojego można korzystać z nowych wersji biblioteki bez konieczności ponownego kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9cc49-141">By adding what is called a [*binding redirect*](https://msdn.microsoft.com/library/7wd6ex19(v=vs.110).aspx) your can use the new library version without having to recompile your app.</span></span> <span data-ttu-id="9cc49-142">W poniższym przykładzie pokazano, jak będzie aktualizował aplikacji `app.config` plik `1.0.1` wersja poprawki `ReferencedLibrary` zamiast `1.0.0` pierwotnie został skompilowany z wersji.</span><span class="sxs-lookup"><span data-stu-id="9cc49-142">The following example shows how you would update your app's `app.config` file to use the `1.0.1` patch version of `ReferencedLibrary` instead of the `1.0.0` version it was originally compiled with.</span></span>

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> <span data-ttu-id="9cc49-143">Ta metoda będzie działać tylko, jeśli nowa wersja `ReferencedLibrary` jest binarny zgodny z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="9cc49-143">This approach will only work if the new version of `ReferencedLibrary` is binary compatible with your app.</span></span>
> <span data-ttu-id="9cc49-144">Zobacz [zgodności z poprzednimi wersjami](#backwards-compatibility) Powyższa sekcja zmian do wyszukania podczas określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="9cc49-144">See the [Backwards Compatibility](#backwards-compatibility) section above for changes to look out for when determining compatibility.</span></span>

### <a name="new"></a><span data-ttu-id="9cc49-145">new</span><span class="sxs-lookup"><span data-stu-id="9cc49-145">new</span></span>

<span data-ttu-id="9cc49-146">Możesz użyć `new` modyfikator, aby ukryć dziedziczone elementy członkowskie klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9cc49-146">You use the `new` modifier to hide inherited members of a base class.</span></span> <span data-ttu-id="9cc49-147">Jest to jeden sposób pochodne mogą odpowiadać na aktualizacje w klasach podstawowych.</span><span class="sxs-lookup"><span data-stu-id="9cc49-147">This is one way derived classes can respond to updates in base classes.</span></span>

<span data-ttu-id="9cc49-148">Wykonaj poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="9cc49-148">Take the following example:</span></span>

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

<span data-ttu-id="9cc49-149">**Output**</span><span class="sxs-lookup"><span data-stu-id="9cc49-149">**Output**</span></span>

```
A base method
A derived method
```

<span data-ttu-id="9cc49-150">W powyższym przykładzie widać, jak `DerivedClass` ukrywa `MyMethod` metody w `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="9cc49-150">From the example above you can see how `DerivedClass` hides the `MyMethod` method present in `BaseClass`.</span></span>
<span data-ttu-id="9cc49-151">Oznacza to, że gdy klasy podstawowej w nowej wersji biblioteki dodaje elementu członkowskiego, który już istnieje w klasie pochodnej, możesz użyć `new` modyfikator użytkownika elementu członkowskiego klasy pochodnej, aby ukryć element członkowski klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="9cc49-151">This means that when a base class in the new version of a library adds a member that already exists in your derived class, you can simply use the `new` modifier on your derived class member to hide the base class member.</span></span>

<span data-ttu-id="9cc49-152">Gdy nie `new` modyfikator jest określony, klasa pochodna domyślnie ukrywa powodujące konflikt elementów członkowskich w klasie podstawowej, chociaż zostaną wygenerowane ostrzeżenie kompilatora nadal kompilacji kodu.</span><span class="sxs-lookup"><span data-stu-id="9cc49-152">When no `new` modifier is specified, a derived class will by default hide conflicting members in a base class, although a compiler warning will be generated the code will still compile.</span></span> <span data-ttu-id="9cc49-153">Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowej wersji biblioteki źródłowym i danych binarnych jest zgodny z kodem, która zależy od niego.</span><span class="sxs-lookup"><span data-stu-id="9cc49-153">This means that simply adding new members to an existing class makes that new version of your library both source and binary compatible with code that depends on it.</span></span>

### <a name="override"></a><span data-ttu-id="9cc49-154">override</span><span class="sxs-lookup"><span data-stu-id="9cc49-154">override</span></span>

<span data-ttu-id="9cc49-155">`override` Modyfikator oznacza pochodnej implementacji rozszerza implementacja elementu członkowskiego klasy podstawowej, a nie ukrywa go.</span><span class="sxs-lookup"><span data-stu-id="9cc49-155">The `override` modifier means a derived implementation extends the implementation of a base class member rather than hides it.</span></span> <span data-ttu-id="9cc49-156">Element członkowski klasy podstawowej musi mieć `virtual` modyfikator zastosować dla niego.</span><span class="sxs-lookup"><span data-stu-id="9cc49-156">The base class member needs to have the `virtual` modifier applied to it.</span></span>

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

<span data-ttu-id="9cc49-157">**Output**</span><span class="sxs-lookup"><span data-stu-id="9cc49-157">**Output**</span></span>

```
Base Method One: Method One
Derived Method One: Derived Method One
```

<span data-ttu-id="9cc49-158">`override` Modyfikator jest obliczane w czasie kompilacji i kompilator zgłosi błąd, jeśli nie znajdzie członka wirtualnego do zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="9cc49-158">The `override` modifier is evaluated at compile time and the compiler will throw an error if it doesn't find a virtual member to override.</span></span>

<span data-ttu-id="9cc49-159">Swoją wiedzę techniki opisano, jak również zrozumienie z jakich sytuacjach do korzystania z nich będzie zdecydowanie do zwiększania łatwość przejścia między wersjami biblioteki.</span><span class="sxs-lookup"><span data-stu-id="9cc49-159">Your knowledge of the discussed techniques as well as your understanding of what situations to use them will go a long way to boost the ease of transition between versions of a library.</span></span>
