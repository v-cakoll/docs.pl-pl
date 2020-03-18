---
title: Przechowywanie wersji i biblioteki .NET
description: Najlepsze zalecenia dotyczące wersji bibliotek .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400401"
---
# <a name="versioning"></a><span data-ttu-id="ad51b-103">Obsługa wersji</span><span class="sxs-lookup"><span data-stu-id="ad51b-103">Versioning</span></span>

<span data-ttu-id="ad51b-104">Biblioteka oprogramowania jest rzadko kompletna w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="ad51b-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="ad51b-105">Dobre biblioteki ewoluują wraz z uchwycone, dodając funkcje, naprawiając błędy i poprawiając wydajność.</span><span class="sxs-lookup"><span data-stu-id="ad51b-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="ad51b-106">Ważne jest, aby można było zwolnić nowe wersje biblioteki .NET, zapewniając dodatkową wartość dla każdej wersji, bez przerywania istniejących użytkowników.</span><span class="sxs-lookup"><span data-stu-id="ad51b-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="ad51b-107">Zmiany powodujące niezgodność</span><span class="sxs-lookup"><span data-stu-id="ad51b-107">Breaking changes</span></span>

<span data-ttu-id="ad51b-108">Aby uzyskać informacje dotyczące obsługi zmian krytycznych między wersjami, zobacz [Zmiany dotyczące podziału](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ad51b-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="ad51b-109">Numery wersji</span><span class="sxs-lookup"><span data-stu-id="ad51b-109">Version numbers</span></span>

<span data-ttu-id="ad51b-110">Biblioteka .NET ma wiele sposobów określania wersji.</span><span class="sxs-lookup"><span data-stu-id="ad51b-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="ad51b-111">Te wersje są najważniejsze:</span><span class="sxs-lookup"><span data-stu-id="ad51b-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="ad51b-112">Wersja pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="ad51b-112">NuGet package version</span></span>

<span data-ttu-id="ad51b-113">[Wersja pakietu NuGet](/nuget/reference/package-versioning) jest wyświetlany na NuGet.org, Visual Studio NuGet menedżera pakietów i jest dodawany do kodu źródłowego, gdy pakiet jest używany.</span><span class="sxs-lookup"><span data-stu-id="ad51b-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="ad51b-114">Wersja pakietu NuGet jest numer wersji, który użytkownicy będą powszechnie widzieć i będą się do niego odwoływać, gdy mówią o wersji biblioteki, z których korzystają.</span><span class="sxs-lookup"><span data-stu-id="ad51b-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="ad51b-115">Wersja pakietu NuGet jest używana przez NuGet i nie ma wpływu na zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ad51b-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="ad51b-116">Identyfikator pakietu NuGet w połączeniu z wersją pakietu NuGet służy do identyfikowania pakietu w NuGet.</span><span class="sxs-lookup"><span data-stu-id="ad51b-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="ad51b-117">Na przykład `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="ad51b-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="ad51b-118">Pakiet z sufiksem jest pakietem w wersji wstępnej i ma specjalne zachowanie, które sprawia, że jest idealny do testowania.</span><span class="sxs-lookup"><span data-stu-id="ad51b-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="ad51b-119">Aby uzyskać więcej informacji, zobacz [Pakiety wersji wstępnej](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="ad51b-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="ad51b-120">Ponieważ wersja pakietu NuGet jest najbardziej widoczną wersją dla deweloperów, warto zaktualizować ją za pomocą [wersji semantycznej (SemVer).](https://semver.org/)</span><span class="sxs-lookup"><span data-stu-id="ad51b-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="ad51b-121">SemVer wskazuje znaczenie zmian między wydaniem i pomaga deweloperom podjąć świadomą decyzję przy wyborze wersji do użycia.</span><span class="sxs-lookup"><span data-stu-id="ad51b-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="ad51b-122">Na przykład przechodzenie od `1.0` do `2.0` wskazuje, że istnieją potencjalnie przełomowe zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad51b-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="ad51b-123">✔️ ZASTANÓW SIĘ przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ad51b-123">✔️ CONSIDER using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="ad51b-124">✔️ używać wersji pakietu NuGet w dokumentacji publicznej, ponieważ jest to numer wersji, który użytkownicy będą często widzieć.</span><span class="sxs-lookup"><span data-stu-id="ad51b-124">✔️ DO use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="ad51b-125">✔️ DO zawierają sufiks w wersji wstępnej podczas zwalniania niestabilnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="ad51b-125">✔️ DO include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="ad51b-126">Użytkownicy muszą zdecydować się na uzyskiwanie pakietów w wersji wstępnej, więc zrozumieją, że pakiet nie został ukończony.</span><span class="sxs-lookup"><span data-stu-id="ad51b-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="ad51b-127">Wersja zestawu</span><span class="sxs-lookup"><span data-stu-id="ad51b-127">Assembly version</span></span>

<span data-ttu-id="ad51b-128">Wersja zestawu jest to, co CLR używa w czasie wykonywania, aby wybrać, która wersja zestawu do załadowania.</span><span class="sxs-lookup"><span data-stu-id="ad51b-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="ad51b-129">Wybranie złożenia przy użyciu wersji dotyczy tylko zestawów o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="ad51b-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="ad51b-130">Windows .NET Framework CLR wymaga dokładnego dopasowania, aby załadować silny nazwany zestaw.</span><span class="sxs-lookup"><span data-stu-id="ad51b-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="ad51b-131">Na przykład `Libary1, Version=1.0.0.0` został skompilowany `Newtonsoft.Json, Version=11.0.0.0`z odniesieniem do .</span><span class="sxs-lookup"><span data-stu-id="ad51b-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="ad51b-132">Program .NET Framework załaduje `11.0.0.0`tylko tę dokładną wersję .</span><span class="sxs-lookup"><span data-stu-id="ad51b-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="ad51b-133">Aby załadować inną wersję w czasie wykonywania, przekierowanie powiązania należy dodać do pliku konfiguracyjnego aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="ad51b-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="ad51b-134">Silne nazewnictwo w połączeniu z wersją złożenia umożliwia [ładowanie wersji zestawu ścisłego.](../assembly/versioning.md)</span><span class="sxs-lookup"><span data-stu-id="ad51b-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="ad51b-135">Podczas silnego nazewnictwa biblioteki ma wiele zalet, często powoduje wyjątki w czasie wykonywania, że zestaw `app.config` / `web.config` nie można odnaleźć i [wymaga powiązań przekierowuje](../../framework/configure-apps/redirect-assembly-versions.md) w zostać naprawione.</span><span class="sxs-lookup"><span data-stu-id="ad51b-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="ad51b-136">Ładowanie zestawu .NET Core zostało złagodzone, a środowisko CLR .NET Core automatycznie załaduje zestawy w czasie wykonywania z wyższą wersją.</span><span class="sxs-lookup"><span data-stu-id="ad51b-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="ad51b-137">✔️ NALEŻY WZIĄĆ tylko w tym wersji głównej w AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="ad51b-137">✔️ CONSIDER only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="ad51b-138">na przykład Biblioteka 1.0 i Biblioteka 1.0.1 mają `1.0.0.0`AssemblyVersion , podczas gdy `2.0.0.0`Biblioteka 2.0 ma AssemblyVersion .</span><span class="sxs-lookup"><span data-stu-id="ad51b-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="ad51b-139">Gdy wersja zestawu zmienia się rzadziej, zmniejsza redirects powiązania.</span><span class="sxs-lookup"><span data-stu-id="ad51b-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="ad51b-140">✔️ NALEŻY ROZWAŻYĆ przechowywanie numer wersji głównej AssemblyVersion i nuget wersji pakietu w synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="ad51b-140">✔️ CONSIDER keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="ad51b-141">AssemblyVersion znajduje się w niektórych komunikatów informacyjnych wyświetlanych użytkownikowi, na przykład nazwy zestawu i zestawu kwalifikowanych nazw typów w komunikatach o wyjątkach.</span><span class="sxs-lookup"><span data-stu-id="ad51b-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="ad51b-142">Utrzymywanie relacji między wersjami zapewnia deweloperom więcej informacji o używanej wersji.</span><span class="sxs-lookup"><span data-stu-id="ad51b-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="ad51b-143">❌NIE mają stałej AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="ad51b-143">❌ DO NOT have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="ad51b-144">Podczas gdy niezmienna AssemblyVersion unika konieczności powiązań przekierowuje, oznacza to, że tylko jedna wersja zestawu może być zainstalowany w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="ad51b-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="ad51b-145">Ponadto aplikacje, które odwołują się do zestawu w GAC zostanie przerwana, jeśli inna aplikacja aktualizuje zestaw GAC z łamania zmian.</span><span class="sxs-lookup"><span data-stu-id="ad51b-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="ad51b-146">Wersja pliku zestawu</span><span class="sxs-lookup"><span data-stu-id="ad51b-146">Assembly file version</span></span>

<span data-ttu-id="ad51b-147">Wersja pliku zestawu służy do wyświetlania wersji pliku w systemie Windows i nie ma wpływu na zachowanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="ad51b-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="ad51b-148">Ustawienie tej wersji jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ad51b-148">Setting this version is optional.</span></span> <span data-ttu-id="ad51b-149">Jest on widoczny w oknie dialogowym Właściwości pliku w Eksploratorze Windows:</span><span class="sxs-lookup"><span data-stu-id="ad51b-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="ad51b-150">![Eksplorator Windows](./media/versioning/win-properties.png "Eksplorator Windows")</span><span class="sxs-lookup"><span data-stu-id="ad51b-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="ad51b-151">✔️ ZAStanów się, w tym numer kompilacji ciągłej integracji jako AssemblyFileVersion wersji.</span><span class="sxs-lookup"><span data-stu-id="ad51b-151">✔️ CONSIDER including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="ad51b-152">Na przykład tworzysz wersję 1.0.0 projektu, a numer kompilacji ciągłej integracji wynosi 99, więc plik FileVersion jest 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="ad51b-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="ad51b-153">✔️ używać formatu `Major.Minor.Build.Revision` dla wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="ad51b-153">✔️ DO use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="ad51b-154">Podczas gdy wersja pliku nigdy nie jest używana przez .NET, [system Windows oczekuje, że wersja pliku](/windows/desktop/menurc/versioninfo-resource) będzie w `Major.Minor.Build.Revision` formacie.</span><span class="sxs-lookup"><span data-stu-id="ad51b-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="ad51b-155">Ostrzeżenie jest wywoływane, jeśli wersja nie jest zgodna z tym formatem.</span><span class="sxs-lookup"><span data-stu-id="ad51b-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="ad51b-156">Wersja informacyjna zestawu</span><span class="sxs-lookup"><span data-stu-id="ad51b-156">Assembly informational version</span></span>

<span data-ttu-id="ad51b-157">Wersja informacyjna zestawu służy do rejestrowania dodatkowych informacji o wersji i nie ma wpływu na zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ad51b-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="ad51b-158">Ustawienie tej wersji jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="ad51b-158">Setting this version is optional.</span></span> <span data-ttu-id="ad51b-159">Jeśli używasz source link, ta wersja zostanie ustawiona na kompilacji z nuget wersji pakietu oraz wersji kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="ad51b-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="ad51b-160">Na przykład `1.0.0-beta1+204ff0a` zawiera skrót zatwierdzania kodu źródłowego, z którego został utworzony zestaw.</span><span class="sxs-lookup"><span data-stu-id="ad51b-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="ad51b-161">Aby uzyskać więcej informacji, zobacz [Łącze źródłowe](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="ad51b-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="ad51b-162">Starsze wersje programu Visual Studio podnieść ostrzeżenie kompilacji, `Major.Minor.Build.Revision`jeśli ta wersja nie jest zgodna z formatem .</span><span class="sxs-lookup"><span data-stu-id="ad51b-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="ad51b-163">Ostrzeżenie można bezpiecznie zignorować.</span><span class="sxs-lookup"><span data-stu-id="ad51b-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="ad51b-164">❌UNIKAJ samodzielnego ustawiania wersji informacyjnej zestawu.</span><span class="sxs-lookup"><span data-stu-id="ad51b-164">❌ AVOID setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="ad51b-165">Zezwalaj sourcelink automatycznie generować wersję zawierającą NuGet i metadanych kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="ad51b-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ad51b-166">[Poprzedni](publish-nuget-package.md)
>[następny](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="ad51b-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
