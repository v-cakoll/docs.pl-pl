---
title: Zależności i biblioteki .NET
description: Zalecenia dotyczące najlepszych rozwiązań związanych z zarządzaniem zależnościami NuGet w bibliotekach platformy .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731482"
---
# <a name="dependencies"></a><span data-ttu-id="b8628-103">Zależności</span><span class="sxs-lookup"><span data-stu-id="b8628-103">Dependencies</span></span>

<span data-ttu-id="b8628-104">Podstawowym sposobem dodawania zależności do biblioteki .NET jest odwoływanie się do pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="b8628-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="b8628-105">Odwołania do pakietów NuGet umożliwiają szybkie ponowne użycie i wykorzystanie już wykorzystanych funkcji, ale są one typowym źródłem tarcia dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b8628-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="b8628-106">Prawidłowe zarządzanie zależnościami jest ważne, aby zapobiec utracie zmian w innych bibliotekach platformy .NET, a na odwrót.</span><span class="sxs-lookup"><span data-stu-id="b8628-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="b8628-107">Zależności rombów</span><span class="sxs-lookup"><span data-stu-id="b8628-107">Diamond dependencies</span></span>

<span data-ttu-id="b8628-108">Jest to typowa sytuacja, w której projekt .NET ma wiele wersji pakietu w jego drzewie zależności.</span><span class="sxs-lookup"><span data-stu-id="b8628-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="b8628-109">Na przykład aplikacja zależy od dwóch pakietów NuGet, z których każda jest zależna od różnych wersji tego samego pakietu.</span><span class="sxs-lookup"><span data-stu-id="b8628-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="b8628-110">Zależność Diamond już istnieje w grafie zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b8628-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="b8628-111">![Zależność Diamond](./media/dependencies/diamond-dependency.png "Zależność Diamond")</span><span class="sxs-lookup"><span data-stu-id="b8628-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="b8628-112">W czasie kompilacji NuGet analizuje wszystkie pakiety, od których zależy projekt, w tym zależności zależności.</span><span class="sxs-lookup"><span data-stu-id="b8628-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="b8628-113">W przypadku wykrycia wielu wersji pakietu reguły są oceniane w celu wybrania jednej z nich.</span><span class="sxs-lookup"><span data-stu-id="b8628-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="b8628-114">Ujednolicenie pakietów jest konieczne, ponieważ uruchomione obok siebie wersje zestawu w tej samej aplikacji są problematyczne w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="b8628-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="b8628-115">Większość zależności diamentów jest łatwo rozwiązywana; mogą jednak tworzyć problemy w pewnych okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="b8628-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="b8628-116">**Sprzeczne odwołania do pakietów NuGet** uniemożliwiają rozpoznanie wersji podczas przywracania pakietu.</span><span class="sxs-lookup"><span data-stu-id="b8628-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="b8628-117">Istotne **zmiany między wersjami** powodują błędy i wyjątki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b8628-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="b8628-118">**Zestaw pakietu ma silną nazwę**, wersja zestawu została zmieniona, a aplikacja jest uruchomiona na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8628-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="b8628-119">Przekierowania powiązań zestawu są wymagane.</span><span class="sxs-lookup"><span data-stu-id="b8628-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="b8628-120">Nie jest możliwe, aby wiedzieć, które pakiety będą używane razem ze swoimi zadaniami.</span><span class="sxs-lookup"><span data-stu-id="b8628-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="b8628-121">Dobrym sposobem na zmniejszenie prawdopodobieństwa, że oddzielenie zależności od rombu w bibliotece polega na zminimalizowaniu liczby pakietów, od których zależą.</span><span class="sxs-lookup"><span data-stu-id="b8628-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="b8628-122">✔️ PRZEPROWADZIĆ przegląd niepotrzebnych zależności w bibliotece platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="b8628-122">✔️ DO review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="b8628-123">Zakresy wersji zależności NuGet</span><span class="sxs-lookup"><span data-stu-id="b8628-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="b8628-124">Odwołanie do pakietu określa zakres prawidłowych pakietów, na które zezwala.</span><span class="sxs-lookup"><span data-stu-id="b8628-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="b8628-125">Zazwyczaj wersja odwołania do pakietu w pliku projektu jest minimalną wersją i nie ma wartości maksymalnej.</span><span class="sxs-lookup"><span data-stu-id="b8628-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="b8628-126">Reguły używane przez NuGet podczas rozpoznawania zależności są [złożone](/nuget/consume-packages/dependency-resolution), ale pakiet NuGet zawsze szuka najniższej stosownej wersji.</span><span class="sxs-lookup"><span data-stu-id="b8628-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="b8628-127">Pakiet NuGet preferuje najniższą odpowiednią wersję w porównaniu z użyciem najwyższej dostępnej, ponieważ najniższa będzie zawierać najmniej problemów ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="b8628-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="b8628-128">Ze względu na najmniejszą odpowiednią regułę wersji programu NuGet nie trzeba umieszczać w odwołaniach do pakietów górnej wersji ani dokładnego zakresu, aby uniknąć pobierania najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="b8628-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="b8628-129">Pakiet NuGet próbuje już znaleźć najmniejszą, najbardziej zgodną wersję.</span><span class="sxs-lookup"><span data-stu-id="b8628-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="b8628-130">Górne ograniczenia wersji spowodują niepowodzenie NuGet w przypadku wystąpienia konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b8628-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="b8628-131">Na przykład jedna biblioteka akceptuje dokładnie 1,0, a inna biblioteka wymaga 2,0 lub wyższej.</span><span class="sxs-lookup"><span data-stu-id="b8628-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="b8628-132">W przypadku wprowadzenia zmian w wersji 2,0, ścisła lub górna zależność wersji gwarantuje błąd.</span><span class="sxs-lookup"><span data-stu-id="b8628-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="b8628-133">![Konflikt zależności rombu](./media/dependencies/diamond-dependency-conflict.png "Konflikt zależności rombu")</span><span class="sxs-lookup"><span data-stu-id="b8628-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="b8628-134">❌ nie mają odwołań do pakietów NuGet bez minimalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b8628-134">❌ DO NOT have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="b8628-135">❌ UNIKAj odwołań do pakietów NuGet, które wymagają dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="b8628-135">❌ AVOID NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="b8628-136">❌ uniknąć odwołań pakietów NuGet z górnym limitem wersji.</span><span class="sxs-lookup"><span data-stu-id="b8628-136">❌ AVOID NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="b8628-137">Pakiety udostępnione dla narzędzia NuGet</span><span class="sxs-lookup"><span data-stu-id="b8628-137">NuGet shared source packages</span></span>

<span data-ttu-id="b8628-138">Jednym ze sposobów zredukowania zewnętrznych zależności pakietów NuGet jest odwołanie do udostępnionych pakietów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="b8628-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="b8628-139">Udostępniony pakiet źródłowy zawiera [pliki kodu źródłowego](/nuget/reference/nuspec#including-content-files) , które są zawarte w projekcie, gdy istnieje odwołanie.</span><span class="sxs-lookup"><span data-stu-id="b8628-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="b8628-140">Ponieważ właśnie umieszczasz pliki kodu źródłowego, które są kompilowane w pozostałej części projektu, nie istnieje zewnętrzna zależność i szansa konfliktu.</span><span class="sxs-lookup"><span data-stu-id="b8628-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="b8628-141">Udostępnione pakiety źródłowe doskonale nadaje się do uwzględnienia małych fragmentów funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b8628-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="b8628-142">Na przykład udostępniony pakiet źródłowy metod pomocników do wykonywania wywołań HTTP.</span><span class="sxs-lookup"><span data-stu-id="b8628-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="b8628-143">![Udostępniony pakiet źródłowy](./media/dependencies/shared-source-package.png "Udostępniony pakiet źródłowy")</span><span class="sxs-lookup"><span data-stu-id="b8628-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="b8628-144">![Udostępniony projekt źródłowy](./media/dependencies/shared-source-project.png "Udostępniony projekt źródłowy")</span><span class="sxs-lookup"><span data-stu-id="b8628-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="b8628-145">Udostępnione pakiety źródłowe mają pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="b8628-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="b8628-146">Można do nich odwoływać się tylko `PackageReference`, więc starsze projekty `packages.config` są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="b8628-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="b8628-147">Współużytkowane pakiety źródłowe są również używane tylko przez projekty o tym samym typie języka.</span><span class="sxs-lookup"><span data-stu-id="b8628-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="b8628-148">Ze względu na to, że udostępnione pakiety źródłowe najlepiej wykorzystać do udostępniania funkcjonalności w ramach projektu typu open source.</span><span class="sxs-lookup"><span data-stu-id="b8628-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="b8628-149">✔️ ROZWAŻYĆ odwołujące się do udostępnionych pakietów źródłowych dla małych, wewnętrznych fragmentów funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b8628-149">✔️ CONSIDER referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="b8628-150">✔️ Rozważ, aby pakiet był udostępnionym pakietem źródłowym, jeśli udostępnia małe, wewnętrzne elementy funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="b8628-150">✔️ CONSIDER making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="b8628-151">✔️ NALEŻY odwoływać się do udostępnionych pakietów źródłowych z `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="b8628-151">✔️ DO reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="b8628-152">To ustawienie informuje program NuGet, że pakiet jest używany tylko w czasie projektowania i nie powinien być ujawniony jako zależność publiczna.</span><span class="sxs-lookup"><span data-stu-id="b8628-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="b8628-153">w publicznym interfejsie API ❌ nie mają udostępnionych typów pakietów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="b8628-153">❌ DO NOT have shared source package types in your public API.</span></span>

> <span data-ttu-id="b8628-154">Współużytkowane typy źródeł są kompilowane do zestawu, do którego się odwołuje, i nie mogą być wymieniane między granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="b8628-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="b8628-155">Na przykład typ `IRepository` udostępnionego źródła w jednym projekcie jest osobnym typem z tego samego udostępnionego źródła `IRepository` w innym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b8628-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="b8628-156">Typy we współużytkowanych pakietach źródłowych powinny mieć widoczność `internal`.</span><span class="sxs-lookup"><span data-stu-id="b8628-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="b8628-157">❌ nie publikować udostępnionych pakietów źródłowych do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="b8628-157">❌ DO NOT publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="b8628-158">Udostępnione pakiety źródłowe zawierają kod źródłowy i mogą być używane tylko przez projekty o tym samym typie języka.</span><span class="sxs-lookup"><span data-stu-id="b8628-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="b8628-159">Na przykład C# udostępniony pakiet źródłowy nie może być używany przez F# aplikację.</span><span class="sxs-lookup"><span data-stu-id="b8628-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="b8628-160">Publikuj udostępnione pakiety źródłowe w [lokalnym kanale informacyjnym lub MyGet](./publish-nuget-package.md) , aby wykorzystać je wewnętrznie w ramach projektu.</span><span class="sxs-lookup"><span data-stu-id="b8628-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b8628-161">[Poprzedni](nuget.md)
>[Następny](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="b8628-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
