---
title: Zależności i biblioteki .NET
description: Najlepsze zalecenia dotyczące zarządzania zależnościami NuGet w bibliotekach .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731482"
---
# <a name="dependencies"></a><span data-ttu-id="b897d-103">Zależności</span><span class="sxs-lookup"><span data-stu-id="b897d-103">Dependencies</span></span>

<span data-ttu-id="b897d-104">Podstawowym sposobem dodawania zależności do biblioteki .NET jest odwoływanie się do pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b897d-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="b897d-105">Odwołania do pakietu NuGet umożliwiają szybkie ponowne użycie i wykorzystanie już zapisanych funkcji, ale są one częstym źródłem tarcia dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b897d-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="b897d-106">Poprawne zarządzanie zależnościami jest ważne, aby zapobiec wprowadzaniu zmian w innych bibliotekach .NET przed przerwaniem biblioteki .NET i odwrotnie!</span><span class="sxs-lookup"><span data-stu-id="b897d-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="b897d-107">Zależności diamentów</span><span class="sxs-lookup"><span data-stu-id="b897d-107">Diamond dependencies</span></span>

<span data-ttu-id="b897d-108">Jest to częsta sytuacja dla projektu .NET mieć wiele wersji pakietu w jego drzewa zależności.</span><span class="sxs-lookup"><span data-stu-id="b897d-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="b897d-109">Na przykład aplikacja zależy od dwóch pakietów NuGet, z których każdy zależy od różnych wersji tego samego pakietu.</span><span class="sxs-lookup"><span data-stu-id="b897d-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="b897d-110">Zależność od diamentów istnieje teraz na wykresie zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b897d-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="b897d-111">![Zależność od diamentów](./media/dependencies/diamond-dependency.png "Zależność od diamentów")</span><span class="sxs-lookup"><span data-stu-id="b897d-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="b897d-112">W czasie kompilacji NuGet analizuje wszystkie pakiety, od których zależy projekt, w tym zależności zależności.</span><span class="sxs-lookup"><span data-stu-id="b897d-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="b897d-113">Po wykryciu wielu wersji pakietu reguły są oceniane, aby wybrać jedną.</span><span class="sxs-lookup"><span data-stu-id="b897d-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="b897d-114">Ujednolicenie pakietów jest konieczne, ponieważ uruchamianie wersji obok siebie zestawu w tej samej aplikacji jest problematyczne w .NET.</span><span class="sxs-lookup"><span data-stu-id="b897d-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="b897d-115">Większość zależności diamentów są łatwo rozwiązane; mogą one jednak powodować problemy w pewnych okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="b897d-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="b897d-116">**Konflikt odwołania nuget pakiet** zapobiec wersji z rozwiązania podczas przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="b897d-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="b897d-117">**Łamanie zmian między wersjami** powoduje błędy i wyjątki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b897d-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="b897d-118">**Zestaw pakietu jest silny o nazwie,** wersja zestawu zmieniona, a aplikacja jest uruchomiona na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b897d-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="b897d-119">Wymagane są przekierowania wiązania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b897d-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="b897d-120">Nie można wiedzieć, jakie pakiety będą używane obok własnych.</span><span class="sxs-lookup"><span data-stu-id="b897d-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="b897d-121">Dobrym sposobem, aby zmniejszyć prawdopodobieństwo podziału zależności diamentbiblioteki jest zminimalizowanie liczby pakietów, od których zależy.</span><span class="sxs-lookup"><span data-stu-id="b897d-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="b897d-122">✔️ do przeglądu biblioteki .NET dla niepotrzebnych zależności.</span><span class="sxs-lookup"><span data-stu-id="b897d-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="b897d-123">Zakresy wersji zależności NuGet</span><span class="sxs-lookup"><span data-stu-id="b897d-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="b897d-124">Odwołanie do pakietu określa zakres prawidłowych pakietów, na które zezwala.</span><span class="sxs-lookup"><span data-stu-id="b897d-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="b897d-125">Zazwyczaj wersja referencyjna pakietu w pliku projektu jest wersją minimalną i nie ma maksymalnej.</span><span class="sxs-lookup"><span data-stu-id="b897d-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="b897d-126">Reguły, które NuGet używa podczas rozwiązywania zależności są [złożone,](/nuget/consume-packages/dependency-resolution)ale NuGet zawsze szuka najniższej wersji odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="b897d-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="b897d-127">NuGet preferuje najniższą odpowiednią wersję niż przy użyciu najwyższej dostępnej, ponieważ najniższy będzie miał najmniej problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="b897d-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="b897d-128">Ze względu na nuget najniższy chorąży reguły wersji, nie jest konieczne umieszczenie górnej wersji lub dokładny zakres na odwołania do pakietu, aby uniknąć uzyskania najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="b897d-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="b897d-129">NuGet już próbuje znaleźć najniższą, najbardziej kompatybilną wersję dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b897d-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="b897d-130">Górne limity wersji spowoduje NuGet nie powiedzie się, jeśli istnieje konflikt.</span><span class="sxs-lookup"><span data-stu-id="b897d-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="b897d-131">Na przykład jedna biblioteka akceptuje dokładnie 1.0, podczas gdy inna biblioteka wymaga 2.0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="b897d-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="b897d-132">Podczas wprowadzania zmian w wersji 2.0, ścisła lub górna zależność wersji limitu gwarantuje błąd.</span><span class="sxs-lookup"><span data-stu-id="b897d-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="b897d-133">![Konflikt zależności diamentów](./media/dependencies/diamond-dependency-conflict.png "Konflikt zależności diamentów")</span><span class="sxs-lookup"><span data-stu-id="b897d-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="b897d-134">❌NIE mają odwołania nuget pakietu bez minimalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b897d-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="b897d-135">❌UNIKAJ nuget odwołań do pakietu, które wymagają dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b897d-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="b897d-136">❌UNIKAJ odwołania do pakietu NuGet z górną granicą wersji.</span><span class="sxs-lookup"><span data-stu-id="b897d-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="b897d-137">NuGet udostępnione pakiety źródłowe</span><span class="sxs-lookup"><span data-stu-id="b897d-137">NuGet shared source packages</span></span>

<span data-ttu-id="b897d-138">Jednym ze sposobów zmniejszenia zewnętrznych zależności pakietów NuGet jest odwołanie się do udostępnionych pakietów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="b897d-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="b897d-139">Udostępniony pakiet źródłowy zawiera [pliki kodu źródłowego,](/nuget/reference/nuspec#including-content-files) które są zawarte w projekcie, gdy odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="b897d-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="b897d-140">Ponieważ po prostu w zestawie plików kodu źródłowego, które są kompilowane z resztą projektu, nie ma żadnych zależności zewnętrznych i prawdopodobieństwo konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b897d-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="b897d-141">Udostępnione pakiety źródłowe są idealne do włączenia małych elementów funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b897d-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="b897d-142">Na przykład udostępniony pakiet źródłowy metod pomocnika do wykonywania wywołań HTTP.</span><span class="sxs-lookup"><span data-stu-id="b897d-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="b897d-143">![Udostępniony pakiet źródłowy](./media/dependencies/shared-source-package.png "Udostępniony pakiet źródłowy")</span><span class="sxs-lookup"><span data-stu-id="b897d-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="b897d-144">![Udostępniony projekt źródłowy](./media/dependencies/shared-source-project.png "Udostępniony projekt źródłowy")</span><span class="sxs-lookup"><span data-stu-id="b897d-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="b897d-145">Udostępnione pakiety źródłowe mają pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="b897d-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="b897d-146">Mogą się do których `PackageReference`odwoływać `packages.config` tylko starsze projekty, więc starsze projekty są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="b897d-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="b897d-147">Również udostępnione pakiety źródłowe są używane tylko przez projekty o tym samym typie języka.</span><span class="sxs-lookup"><span data-stu-id="b897d-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="b897d-148">Ze względu na te ograniczenia udostępnione pakiety źródłowe najlepiej są używane do udostępniania funkcji w projekcie open source.</span><span class="sxs-lookup"><span data-stu-id="b897d-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="b897d-149">✔️ ROZWAŻ odwoływanie się do udostępnionych pakietów źródłowych dla małych, wewnętrznych elementów funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b897d-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="b897d-150">✔️ ROZWAŻ uczynienie pakietu udostępnionym pakietem źródłowym, jeśli zapewnia on małe, wewnętrzne elementy funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b897d-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="b897d-151">✔️ do odwoływania `PrivateAssets="All"`się do udostępnionych pakietów źródłowych z .</span><span class="sxs-lookup"><span data-stu-id="b897d-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="b897d-152">To ustawienie informuje NuGet pakiet ma być używany tylko w czasie rozwoju i nie powinny być udostępniane jako zależności publicznej.</span><span class="sxs-lookup"><span data-stu-id="b897d-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="b897d-153">❌NIE mają współużytkowanych typów pakietów źródłowych w publicznym interfejsie API.</span><span class="sxs-lookup"><span data-stu-id="b897d-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="b897d-154">Udostępnione typy źródeł są kompilowane do zestawu odwołań i nie mogą być wymieniane przez granice zestawu.</span><span class="sxs-lookup"><span data-stu-id="b897d-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="b897d-155">Na przykład typu udostępnionego źródła `IRepository` w jednym projekcie jest oddzielnytyp `IRepository` z tego samego źródła udostępnionego w innym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b897d-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="b897d-156">Typy w udostępnionych pakietach źródłowych `internal` powinny mieć widoczność.</span><span class="sxs-lookup"><span data-stu-id="b897d-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="b897d-157">❌NIE publikuj udostępnionych pakietów źródłowych w celu NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="b897d-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="b897d-158">Udostępnione pakiety źródłowe zawierają kod źródłowy i mogą być używane tylko przez projekty o tym samym typie języka.</span><span class="sxs-lookup"><span data-stu-id="b897d-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="b897d-159">Na przykład pakiet źródłowy współużytkowane C# nie może być używany przez aplikację F#.</span><span class="sxs-lookup"><span data-stu-id="b897d-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="b897d-160">Publikowanie udostępnionych pakietów źródłowych w [lokalnym źródle danych lub MyGet,](./publish-nuget-package.md) aby zużywać je wewnętrznie w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b897d-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b897d-161">[Poprzedni](nuget.md)
>[następny](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="b897d-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
