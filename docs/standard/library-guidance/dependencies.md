---
title: Zależności i bibliotek platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań do zarządzania zależności NuGet w bibliotekach .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0cd00ff36ad52bc46769ca1793b9efd02db14da1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644275"
---
# <a name="dependencies"></a><span data-ttu-id="55ee3-103">Zależności</span><span class="sxs-lookup"><span data-stu-id="55ee3-103">Dependencies</span></span>

<span data-ttu-id="55ee3-104">Podstawowym sposobem dodawania zależności do biblioteki .NET odwołuje się do pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="55ee3-104">The primary way of adding dependencies to a .NET library is referencing NuGet packages.</span></span> <span data-ttu-id="55ee3-105">Odwołania do pakietu NuGet pozwalają na szybkie ponowne użycie i korzystać z funkcji już napisane, ale są one wspólne źródło zajmowania się dla deweloperów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="55ee3-105">NuGet package references allow you to quickly reuse and leverage already written functionality, but they're a common source of friction for .NET developers.</span></span> <span data-ttu-id="55ee3-106">Poprawnie Zarządzanie zależnościami ważne jest, aby zapobiegać zmianom w innych bibliotekach .NET przed przerwaniem działania biblioteki .NET i na odwrót!</span><span class="sxs-lookup"><span data-stu-id="55ee3-106">Correctly managing dependencies is important to prevent changes in other .NET libraries from breaking your .NET library, and vice versa!</span></span>

## <a name="diamond-dependencies"></a><span data-ttu-id="55ee3-107">Zależności romb</span><span class="sxs-lookup"><span data-stu-id="55ee3-107">Diamond dependencies</span></span>

<span data-ttu-id="55ee3-108">To sytuacja wspólne dla projektu .NET wiele wersji pakietu w jego drzewie zależności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-108">It's a common situation for a .NET project to have multiple versions of a package in its dependency tree.</span></span> <span data-ttu-id="55ee3-109">Na przykład aplikacja jest zależna od dwóch pakietów NuGet, z których każdy jest zależna od różne wersje tego samego pakietu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-109">For example, an app depends on two NuGet packages, each of which depends on different versions of the same package.</span></span> <span data-ttu-id="55ee3-110">Obecnie istnieje zależność romb w wykres zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-110">A diamond dependency now exists in the app's dependency graph.</span></span>

<span data-ttu-id="55ee3-111">![Romboidalny zależności](./media/dependencies/diamond-dependency.png "romboidalna zależności")</span><span class="sxs-lookup"><span data-stu-id="55ee3-111">![Diamond dependency](./media/dependencies/diamond-dependency.png "Diamond dependency")</span></span>

<span data-ttu-id="55ee3-112">W czasie kompilacji NuGet analizuje wszystkie pakiety, które projekt zależy, wraz z zależnościami zależności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-112">At build time, NuGet analyzes all the packages that a project depends on, including the dependencies of dependencies.</span></span> <span data-ttu-id="55ee3-113">Po wykryciu wiele wersji pakietu do pobrania jednego oceniania reguł.</span><span class="sxs-lookup"><span data-stu-id="55ee3-113">When multiple versions of a package are detected, rules are evaluated to pick one.</span></span> <span data-ttu-id="55ee3-114">Pakiety, ujednolicając naukę jest konieczne w przypadku, ponieważ wersjami side-by-side zestawu w tej samej aplikacji jest problematyczne na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="55ee3-114">Unifying packages is necessary because running side-by-side versions of an assembly in the same application is problematic in .NET.</span></span>

<span data-ttu-id="55ee3-115">Większość zależności romb łatwo są rozwiązywane; jednak ich może prowadzić do problemów w pewnych okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="55ee3-115">Most diamond dependencies are easily resolved; however, they can create issues in certain circumstances:</span></span>

1. <span data-ttu-id="55ee3-116">**Odwołania do pakietu NuGet powodujące konflikt** uniemożliwić wersji rozwiązania podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="55ee3-116">**Conflicting NuGet package references** prevent a version from being resolved during package restore.</span></span>
2. <span data-ttu-id="55ee3-117">**Fundamentalne zmiany między wersjami** powodować błędy i wyjątki w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55ee3-117">**Breaking changes between the versions** cause bugs and exceptions at runtime.</span></span>
3. <span data-ttu-id="55ee3-118">**Zestaw pakietów ma silną nazwę**, zmianie wersji zestawu, a aplikacja jest uruchomiona w środowisku .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="55ee3-118">**The package assembly is strong named**, the assembly version changed, and the app is running on the .NET Framework.</span></span> <span data-ttu-id="55ee3-119">Przekierowania powiązań zestawu są wymagane.</span><span class="sxs-lookup"><span data-stu-id="55ee3-119">Assembly binding redirects are required.</span></span>

<span data-ttu-id="55ee3-120">Nie jest możliwe, należy wiedzieć, jakie pakiety będą używać razem z własnych.</span><span class="sxs-lookup"><span data-stu-id="55ee3-120">It's not possible to know what packages will be used alongside your own.</span></span> <span data-ttu-id="55ee3-121">Dobrym sposobem zmniejszenia prawdopodobieństwa zależność romb istotne biblioteki jest zminimalizowanie liczby pakietów, które zależą od.</span><span class="sxs-lookup"><span data-stu-id="55ee3-121">A good way to reduce the likelihood of a diamond dependency breaking your library is to minimize the number of packages you depend on.</span></span>

<span data-ttu-id="55ee3-122">**CZY ✔️** Przejrzyj biblioteki .NET niepotrzebne zależności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-122">**✔️ DO** review your .NET library for unnecessary dependencies.</span></span>

## <a name="nuget-dependency-version-ranges"></a><span data-ttu-id="55ee3-123">Zakresów wersji zależności NuGet</span><span class="sxs-lookup"><span data-stu-id="55ee3-123">NuGet dependency version ranges</span></span>

<span data-ttu-id="55ee3-124">Odwołanie do pakietu określa zakres prawidłowy pakietów, które będzie ona zezwalała.</span><span class="sxs-lookup"><span data-stu-id="55ee3-124">A package reference specifies the range of valid packages it allows.</span></span> <span data-ttu-id="55ee3-125">Zazwyczaj wersja odwołanie do pakietu w pliku projektu jest minimalną wersją, a jest brak maksimum.</span><span class="sxs-lookup"><span data-stu-id="55ee3-125">Typically, the package reference version in the project file is the minimum version and there's no maximum.</span></span>

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

<span data-ttu-id="55ee3-126">Dostępne są następujące reguły, których NuGet używa podczas rozpoznawania zależności [złożonych](/nuget/consume-packages/dependency-resolution), ale NuGet zawsze szuka najniższą odpowiedniej wersji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-126">The rules that NuGet uses when resolving dependencies are [complex](/nuget/consume-packages/dependency-resolution), but NuGet always looks for the lowest applicable version.</span></span> <span data-ttu-id="55ee3-127">NuGet preferuje najniższy odpowiednią wersję przy użyciu najwyższej dostępności, ponieważ najniższa będzie miał co najmniej problemy ze zgodnością.</span><span class="sxs-lookup"><span data-stu-id="55ee3-127">NuGet prefers the lowest applicable version over using the highest available because the lowest will have the least compatibility issues.</span></span>

<span data-ttu-id="55ee3-128">Ze względu na najniższym reguły odpowiedniej wersji NuGet nie jest niezbędna do umieszczenia w wersji górny lub dokładny zakres na odwołania do pakietu, aby uniknąć pobierania najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-128">Because of NuGet's lowest applicable version rule, it isn't necessary to place an upper version or exact range on package references to avoid getting the latest version.</span></span> <span data-ttu-id="55ee3-129">NuGet już próbuje znaleźć najniższej i najbardziej zgodnej wersji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-129">NuGet already tries to find the lowest, most compatible version for you.</span></span>

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

<span data-ttu-id="55ee3-130">Limity górny wersji spowoduje, że rozszerzenie NuGet, aby zakończyć się niepowodzeniem, jeśli występuje konflikt.</span><span class="sxs-lookup"><span data-stu-id="55ee3-130">Upper version limits will cause NuGet to fail if there's a conflict.</span></span> <span data-ttu-id="55ee3-131">Na przykład jedna biblioteka przyjmuje dokładnie 1.0 innej biblioteki wymaga 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="55ee3-131">For example, one library accepts exactly 1.0 while another library requires 2.0 or above.</span></span> <span data-ttu-id="55ee3-132">Gdy przełomowe zmiany mogły zostać wprowadzone w wersji 2.0, zależność wersji strict lub górny limit gwarantuje błąd.</span><span class="sxs-lookup"><span data-stu-id="55ee3-132">While breaking changes may have been introduced in version 2.0, a strict or upper limit version dependency guarantees an error.</span></span>

<span data-ttu-id="55ee3-133">![Romboidalna konfliktów zależności](./media/dependencies/diamond-dependency-conflict.png "romboidalna konfliktów zależności")</span><span class="sxs-lookup"><span data-stu-id="55ee3-133">![Diamond dependency conflict](./media/dependencies/diamond-dependency-conflict.png "Diamond dependency conflict")</span></span>

<span data-ttu-id="55ee3-134">**❌ NIE** ma odwołania do pakietu NuGet bez ograniczeń minimalnej wersji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-134">**❌ DO NOT** have NuGet package references with no minimum version.</span></span>

<span data-ttu-id="55ee3-135">**Należy UNIKAĆ ❌** odwołania do pakietu NuGet, wymagających dokładna wersja.</span><span class="sxs-lookup"><span data-stu-id="55ee3-135">**❌ AVOID** NuGet package references that demand an exact version.</span></span>

<span data-ttu-id="55ee3-136">**Należy UNIKAĆ ❌** odwołania do pakietu NuGet za pomocą wersji z górnego limitu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-136">**❌ AVOID** NuGet package references with a version upper limit.</span></span>

## <a name="nuget-shared-source-packages"></a><span data-ttu-id="55ee3-137">NuGet udostępnione źródła pakietów</span><span class="sxs-lookup"><span data-stu-id="55ee3-137">NuGet shared source packages</span></span>

<span data-ttu-id="55ee3-138">Jest jednym ze sposobów, aby zmniejszyć zewnętrznych zależności pakietów NuGet do odwołania się do udostępnionego źródła pakietów.</span><span class="sxs-lookup"><span data-stu-id="55ee3-138">One way to reduce external NuGet package dependencies is to reference shared source packages.</span></span> <span data-ttu-id="55ee3-139">Pakiet źródłowy udostępniony zawiera [pliki kodów źródłowych](/nuget/reference/nuspec#including-content-files) uwzględnianych w przypadku odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-139">A shared source package contains [source code files](/nuget/reference/nuspec#including-content-files) that are included in a project when referenced.</span></span> <span data-ttu-id="55ee3-140">Ponieważ one po prostu łącznie z plików kodu źródłowego, które są kompilowane z pozostałą częścią projektu, jest nie zależności zewnętrznych oraz prawdopodobieństwo konfliktu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-140">Because you're just including source code files that are compiled with the rest of your project, there's no external dependency and chance of conflict.</span></span>

<span data-ttu-id="55ee3-141">Udostępnione źródło, które pakiety są doskonale sprawdza się w tym małe fragmenty funkcji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-141">Shared source packages are great for including small pieces of functionality.</span></span> <span data-ttu-id="55ee3-142">Na przykład pakiet źródłowy udostępniony metody pomocnika do nawiązywania połączeń HTTP.</span><span class="sxs-lookup"><span data-stu-id="55ee3-142">For example, a shared source package of helper methods for making HTTP calls.</span></span>

<span data-ttu-id="55ee3-143">![Pakiet "source" Shared](./media/dependencies/shared-source-package.png "udostępnione źródła pakietu")</span><span class="sxs-lookup"><span data-stu-id="55ee3-143">![Shared source package](./media/dependencies/shared-source-package.png "Shared source package")</span></span>

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

<span data-ttu-id="55ee3-144">![Projekt źródłowy współużytkowanego](./media/dependencies/shared-source-project.png "projekt źródłowy współużytkowanego")</span><span class="sxs-lookup"><span data-stu-id="55ee3-144">![Shared source project](./media/dependencies/shared-source-project.png "Shared source project")</span></span>

<span data-ttu-id="55ee3-145">Źródłowy udostępniony pakiety mają pewne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="55ee3-145">Shared source packages have some limitations.</span></span> <span data-ttu-id="55ee3-146">One mogą być przywoływane tylko przez `PackageReference`, więc starsze `packages.config` projekty są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="55ee3-146">They can only be referenced by `PackageReference`, so older `packages.config` projects are excluded.</span></span> <span data-ttu-id="55ee3-147">Pakiety źródłowy udostępniony tylko są również może być używany przez projektów za pomocą tego samego typu języka.</span><span class="sxs-lookup"><span data-stu-id="55ee3-147">Also shared source packages are only usable by projects with the same language type.</span></span> <span data-ttu-id="55ee3-148">Ze względu na ograniczenia te pakiety źródłowy udostępniony najlepiej sprawdzają się udostępniania funkcji w ramach projektu open source.</span><span class="sxs-lookup"><span data-stu-id="55ee3-148">Because of these limitations shared source packages are best used to share functionality within an open-source project.</span></span>

<span data-ttu-id="55ee3-149">**ROZWAŻ ✔️** odwołuje się do udostępnionego źródła pakietów dla małych, wewnętrzne elementy funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-149">**✔️ CONSIDER** referencing shared source packages for small, internal pieces of functionality.</span></span>

<span data-ttu-id="55ee3-150">**ROZWAŻ ✔️** co pakiet źródłowy udostępniony pakiet zapewnia małe, wewnętrzne elementy funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-150">**✔️ CONSIDER** making your package a shared source package if it provides small, internal pieces of functionality.</span></span>

<span data-ttu-id="55ee3-151">**CZY ✔️** odwołania się do udostępnionego źródła pakietów przy użyciu `PrivateAssets="All"`.</span><span class="sxs-lookup"><span data-stu-id="55ee3-151">**✔️ DO** reference shared source packages with `PrivateAssets="All"`.</span></span>

> <span data-ttu-id="55ee3-152">To ustawienie określa pakiet NuGet tylko ma być używany w czasie tworzenia i nie powinien być udostępniany jako publicznego zależności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-152">This setting tells NuGet the package is only to be used at development time and shouldn't be exposed as a public dependency.</span></span>

<span data-ttu-id="55ee3-153">**❌ NIE** udostępnionego źródła typów pakietów w publicznego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="55ee3-153">**❌ DO NOT** have shared source package types in your public API.</span></span>

> <span data-ttu-id="55ee3-154">Udostępnione źródło typy są kompilowane do zestawu odwołującego się i nie można wymienić poza granicami zestawu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-154">Shared source types are compiled into the referencing assembly and can't be exchanged across assembly boundaries.</span></span> <span data-ttu-id="55ee3-155">Na przykład udostępniane source `IRepository` typ w jednym projekcie to oddzielne z tego samego udostępnionego źródła `IRepository` w innym projekcie.</span><span class="sxs-lookup"><span data-stu-id="55ee3-155">For example, a shared-source `IRepository` type in one project is a separate type from the same shared-source `IRepository` in another project.</span></span> <span data-ttu-id="55ee3-156">Typy w pakietach źródłowy udostępniony powinny mieć `internal` widoczności.</span><span class="sxs-lookup"><span data-stu-id="55ee3-156">Types in shared source packages should have an `internal` visibility.</span></span>

<span data-ttu-id="55ee3-157">**❌ NIE** Publikowanie pakietów źródłowy udostępniony na stronie NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="55ee3-157">**❌ DO NOT** publish shared source packages to NuGet.org.</span></span>

> <span data-ttu-id="55ee3-158">Udostępnione źródło pakiety zawierają kod źródłowy i mogą być używane tylko przez projektów za pomocą tego samego typu języka.</span><span class="sxs-lookup"><span data-stu-id="55ee3-158">Shared source packages contain source code and can only be used by projects with the same language type.</span></span> <span data-ttu-id="55ee3-159">Na przykład C# udostępnionego źródła pakietu nie może używać F# aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55ee3-159">For example, a C# shared source package cannot be used by an F# application.</span></span>
>
> <span data-ttu-id="55ee3-160">Publikowanie pakietów źródłowy udostępniony na [lokalne źródła danych lub MyGet](./publish-nuget-package.md) do korzystania z nich wewnętrznie w obrębie projektu.</span><span class="sxs-lookup"><span data-stu-id="55ee3-160">Publish shared source packages to a [local feed or MyGet](./publish-nuget-package.md) to consume them internally within your project.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="55ee3-161">[Poprzednie](nuget.md)
>[dalej](sourcelink.md)</span><span class="sxs-lookup"><span data-stu-id="55ee3-161">[Previous](nuget.md)
[Next](sourcelink.md)</span></span>
