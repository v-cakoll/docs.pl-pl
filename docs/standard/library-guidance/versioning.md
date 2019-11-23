---
title: Przechowywanie wersji i biblioteki .NET
description: Zalecenia dotyczące zgodności z wersjami bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: 9250e48707c0ea72cdf8bef9663f5a3516309b86
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969009"
---
# <a name="versioning"></a><span data-ttu-id="2b96e-103">Przechowywanie wersji</span><span class="sxs-lookup"><span data-stu-id="2b96e-103">Versioning</span></span>

<span data-ttu-id="2b96e-104">Biblioteka oprogramowania jest rzadko kompletna w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="2b96e-104">A software library is rarely complete in version 1.0.</span></span> <span data-ttu-id="2b96e-105">Dobre biblioteki są rozwijane wraz z upływem czasu, Dodawanie funkcji, naprawianie usterek i Poprawianie wydajności.</span><span class="sxs-lookup"><span data-stu-id="2b96e-105">Good libraries evolve over time, adding features, fixing bugs and improving performance.</span></span> <span data-ttu-id="2b96e-106">Ważne jest, aby można było wydać nowe wersje biblioteki .NET, zapewniając dodatkową wartość w każdej wersji, bez przerywania istniejących użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2b96e-106">It is important that you can release new versions of a .NET library, providing additional value with each version, without breaking existing users.</span></span>

## <a name="breaking-changes"></a><span data-ttu-id="2b96e-107">Fundamentalne zmiany</span><span class="sxs-lookup"><span data-stu-id="2b96e-107">Breaking changes</span></span>

<span data-ttu-id="2b96e-108">Aby uzyskać informacje na temat obsługi istotnych zmian między wersjami, zobacz artykuł dotyczący [zmiany](./breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="2b96e-108">For information about handling breaking changes between versions, see [Breaking changes](./breaking-changes.md).</span></span>

## <a name="version-numbers"></a><span data-ttu-id="2b96e-109">Numery wersji</span><span class="sxs-lookup"><span data-stu-id="2b96e-109">Version numbers</span></span>

<span data-ttu-id="2b96e-110">Biblioteka .NET ma wiele sposobów na określenie wersji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-110">A .NET library has many ways to specify a version.</span></span> <span data-ttu-id="2b96e-111">Te wersje są najważniejsze:</span><span class="sxs-lookup"><span data-stu-id="2b96e-111">These versions are the most important:</span></span>

### <a name="nuget-package-version"></a><span data-ttu-id="2b96e-112">Wersja pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="2b96e-112">NuGet package version</span></span>

<span data-ttu-id="2b96e-113">[Wersja pakietu NuGet](/nuget/reference/package-versioning) jest wyświetlana w NuGet.org, menedżerze pakietów NuGet programu Visual Studio i jest dodawana do kodu źródłowego, gdy używany jest pakiet.</span><span class="sxs-lookup"><span data-stu-id="2b96e-113">The [NuGet package version](/nuget/reference/package-versioning) is displayed on NuGet.org, the Visual Studio NuGet package manager, and is added to source code when the package is used.</span></span> <span data-ttu-id="2b96e-114">Wersja pakietu NuGet to numer wersji, który użytkownicy często zobaczą, i odwołują się do niego podczas rozmowy o wersji biblioteki, z której korzystają.</span><span class="sxs-lookup"><span data-stu-id="2b96e-114">The NuGet package version is the version number users will commonly see, and they'll refer to it when they talk about the version of a library they're using.</span></span> <span data-ttu-id="2b96e-115">Wersja pakietu NuGet jest używana przez program NuGet i nie ma wpływu na zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b96e-115">The NuGet package version is used by NuGet and has no effect on runtime behavior.</span></span>

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

<span data-ttu-id="2b96e-116">Identyfikator pakietu NuGet połączony z wersją pakietu NuGet jest używany do identyfikowania pakietu w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b96e-116">The NuGet package identifier combined with the NuGet package version is used to identify a package in NuGet.</span></span> <span data-ttu-id="2b96e-117">Na przykład `Newtonsoft.Json` + `11.0.2`.</span><span class="sxs-lookup"><span data-stu-id="2b96e-117">For example, `Newtonsoft.Json` + `11.0.2`.</span></span> <span data-ttu-id="2b96e-118">Pakiet z sufiksem jest pakietem wersji wstępnej i ma specjalne zachowanie, które sprawia, że jest idealnym rozwiązaniem do testowania.</span><span class="sxs-lookup"><span data-stu-id="2b96e-118">A package with a suffix is a pre-release package and has special behavior that makes it ideal for testing.</span></span> <span data-ttu-id="2b96e-119">Aby uzyskać więcej informacji, zobacz [pakiety wersji wstępnej](./nuget.md#pre-release-packages).</span><span class="sxs-lookup"><span data-stu-id="2b96e-119">For more information, see [Pre-release packages](./nuget.md#pre-release-packages).</span></span>

<span data-ttu-id="2b96e-120">Ponieważ wersja pakietu NuGet jest najbardziej widoczną wersją dla deweloperów, dobrym pomysłem jest zaktualizowanie go przy użyciu [wersji semantycznej (SemVer)](https://semver.org/).</span><span class="sxs-lookup"><span data-stu-id="2b96e-120">Because the NuGet package version is the most visible version to developers, it's a good idea to update it using [Semantic Versioning (SemVer)](https://semver.org/).</span></span> <span data-ttu-id="2b96e-121">SemVer wskazuje istotność zmian między wydaniem i pomaga deweloperom podejmować świadome decyzje podczas wybierania używanej wersji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-121">SemVer indicates the significance of changes between release and helps developers make an informed decision when choosing what version to use.</span></span> <span data-ttu-id="2b96e-122">Na przykład przechodzenie z `1.0` do `2.0` wskazuje, że istnieją potencjalne zmiany.</span><span class="sxs-lookup"><span data-stu-id="2b96e-122">For example, going from `1.0` to `2.0` indicates that there are potentially breaking changes.</span></span>

<span data-ttu-id="2b96e-123">**✔️ rozważyć** użycie programu [SemVer 2.0.0](https://semver.org/) w celu uzyskania wersji pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="2b96e-123">**✔️ CONSIDER** using [SemVer 2.0.0](https://semver.org/) to version your NuGet package.</span></span>

<span data-ttu-id="2b96e-124">**✔️** używać wersji pakietu NuGet w publicznej dokumentacji, ponieważ jest to numer wersji, który użytkownicy często zobaczą.</span><span class="sxs-lookup"><span data-stu-id="2b96e-124">**✔️ DO** use the NuGet package version in public documentation as it's the version number that users will commonly see.</span></span>

<span data-ttu-id="2b96e-125">**✔️** uwzględnić sufiks wstępnej wersji podczas zwalniania niestabilnego pakietu.</span><span class="sxs-lookup"><span data-stu-id="2b96e-125">**✔️ DO** include a pre-release suffix when releasing a non-stable package.</span></span>

> <span data-ttu-id="2b96e-126">Użytkownicy muszą wyrazić zgodę na pobranie pakietów w wersji wstępnej, aby zrozumieć, że pakiet nie został ukończony.</span><span class="sxs-lookup"><span data-stu-id="2b96e-126">Users must opt in to getting pre-release packages, so they will understand that the package is not complete.</span></span>

### <a name="assembly-version"></a><span data-ttu-id="2b96e-127">Wersja zestawu</span><span class="sxs-lookup"><span data-stu-id="2b96e-127">Assembly version</span></span>

<span data-ttu-id="2b96e-128">Wersja zestawu jest używany przez środowisko CLR w czasie wykonywania, aby wybrać wersję zestawu do załadowania.</span><span class="sxs-lookup"><span data-stu-id="2b96e-128">The assembly version is what the CLR uses at runtime to select which version of an assembly to load.</span></span> <span data-ttu-id="2b96e-129">Wybór zestawu przy użyciu wersji ma zastosowanie tylko do zestawów o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2b96e-129">Selecting an assembly using versioning only applies to assemblies with a strong name.</span></span>

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

<span data-ttu-id="2b96e-130">Środowisko CLR systemu Windows .NET Framework wymaga dokładnego dopasowania, aby załadować zestaw o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2b96e-130">The Windows .NET Framework CLR demands an exact match to load a strong named assembly.</span></span> <span data-ttu-id="2b96e-131">Na przykład `Libary1, Version=1.0.0.0` został skompilowany z odwołaniem do `Newtonsoft.Json, Version=11.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="2b96e-131">For example, `Libary1, Version=1.0.0.0` was compiled with a reference to `Newtonsoft.Json, Version=11.0.0.0`.</span></span> <span data-ttu-id="2b96e-132">.NET Framework będzie ładować tylko dokładne `11.0.0.0`wersji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-132">The .NET Framework will only load that exact version `11.0.0.0`.</span></span> <span data-ttu-id="2b96e-133">Aby załadować inną wersję w czasie wykonywania, należy dodać przekierowanie powiązania do pliku konfiguracji aplikacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2b96e-133">To load a different version at runtime, a binding redirect must be added to the .NET application's config file.</span></span>

<span data-ttu-id="2b96e-134">Silne nazewnictwo połączone z wersją zestawu umożliwia [ścisłe ładowanie wersji zestawu](../assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="2b96e-134">Strong naming combined with assembly version enables [strict assembly version loading](../assembly/versioning.md).</span></span> <span data-ttu-id="2b96e-135">Chociaż silne nazewnictwo biblioteki ma wiele korzyści, często są to wyjątki w czasie wykonywania, których nie można odnaleźć zestawu i [wymaga nawiązania powiązań](../../framework/configure-apps/redirect-assembly-versions.md) w `app.config`/`web.config` zostać naprawiony.</span><span class="sxs-lookup"><span data-stu-id="2b96e-135">While strong naming a library has a number of benefits, it often results in runtime exceptions that an assembly can't be found and [requires binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) in `app.config`/`web.config` to be fixed.</span></span> <span data-ttu-id="2b96e-136">Ładowanie zestawu .NET Core jest swobodne i program .NET Core CLR automatycznie ładuje zestawy w środowisku uruchomieniowym o wyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-136">.NET Core assembly loading has been relaxed, and the .NET Core CLR will automatically load assemblies at runtime with a higher version.</span></span>

<span data-ttu-id="2b96e-137">**✔️ rozważyć** tylko wersję główną w AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="2b96e-137">**✔️ CONSIDER** only including a major version in the AssemblyVersion.</span></span>

> <span data-ttu-id="2b96e-138">na przykład biblioteka 1,0 i Biblioteka 1.0.1 mają AssemblyVersion `1.0.0.0`, podczas gdy biblioteka 2,0 ma AssemblyVersion `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="2b96e-138">e.g. Library 1.0 and Library 1.0.1 both have an AssemblyVersion of `1.0.0.0`, while Library 2.0 has AssemblyVersion of `2.0.0.0`.</span></span> <span data-ttu-id="2b96e-139">Gdy wersja zestawu zmienia się rzadziej, zmniejsza przekierowania powiązań.</span><span class="sxs-lookup"><span data-stu-id="2b96e-139">When the assembly version changes less often, it reduces binding redirects.</span></span>

<span data-ttu-id="2b96e-140">**✔️ rozważyć** utrzymywanie głównego numeru wersji AssemblyVersion i wersji pakietu NuGet w synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-140">**✔️ CONSIDER** keeping the major version number of the AssemblyVersion and the NuGet package version in sync.</span></span>

> <span data-ttu-id="2b96e-141">AssemblyVersion jest dołączany do niektórych komunikatów informacyjnych wyświetlanych użytkownikowi, np. Nazwa zestawu i nazwy typów kwalifikowana zestawu w komunikatach o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2b96e-141">The AssemblyVersion is included in some informational messages displayed to the user, e.g. the assembly name and assembly qualified type names in exception messages.</span></span> <span data-ttu-id="2b96e-142">Utrzymywanie relacji między wersjami zapewnia deweloperom więcej informacji na temat używanej wersji.</span><span class="sxs-lookup"><span data-stu-id="2b96e-142">Maintaining a relationship between the versions provides more information to developers about which version they are using.</span></span>

<span data-ttu-id="2b96e-143">**❌ Nie** ma stałej AssemblyVersion.</span><span class="sxs-lookup"><span data-stu-id="2b96e-143">**❌ DO NOT** have a fixed AssemblyVersion.</span></span>

> <span data-ttu-id="2b96e-144">Podczas gdy AssemblyVersion nie zmienia się potrzeba przekierowania powiązań, oznacza to, że tylko jedna wersja zestawu może być zainstalowana w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="2b96e-144">While an unchanging AssemblyVersion avoids the need for binding redirects, it means that only a single version of the assembly can be installed in the Global Assembly Cache (GAC).</span></span> <span data-ttu-id="2b96e-145">Ponadto aplikacje odwołujące się do zestawu w pamięci podręcznej GAC zostaną przerwane, jeśli inna aplikacja zaktualizuje zestaw GAC przy użyciu istotnych zmian.</span><span class="sxs-lookup"><span data-stu-id="2b96e-145">Also, the applications that reference the assembly in the GAC will break if another application updates the GAC assembly with breaking changes.</span></span>

### <a name="assembly-file-version"></a><span data-ttu-id="2b96e-146">Wersja pliku zestawu</span><span class="sxs-lookup"><span data-stu-id="2b96e-146">Assembly file version</span></span>

<span data-ttu-id="2b96e-147">Wersja pliku zestawu jest używana do wyświetlania wersji pliku w systemie Windows i nie ma wpływu na zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b96e-147">The assembly file version is used to display a file version in Windows and has no effect on runtime behavior.</span></span> <span data-ttu-id="2b96e-148">Ustawienie tej wersji jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="2b96e-148">Setting this version is optional.</span></span> <span data-ttu-id="2b96e-149">Jest on widoczny w oknie dialogowym właściwości pliku w Eksploratorze Windows:</span><span class="sxs-lookup"><span data-stu-id="2b96e-149">It's visible in the File Properties dialog in Windows Explorer:</span></span>

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

<span data-ttu-id="2b96e-150">Eksplorator ![Windows Eksplorator](./media/versioning/win-properties.png "systemu") Windows</span><span class="sxs-lookup"><span data-stu-id="2b96e-150">![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")</span></span>

<span data-ttu-id="2b96e-151">**✔️ rozważyć** uwzględnienie numeru kompilacji ciągłej integracji jako poprawki AssemblyFileVersion.</span><span class="sxs-lookup"><span data-stu-id="2b96e-151">**✔️ CONSIDER** including a continuous integration build number as the AssemblyFileVersion revision.</span></span>

> <span data-ttu-id="2b96e-152">Załóżmy na przykład, że tworzysz wersję 1.0.0 projektu, a numer kompilacji ciągłej integracji to 99, a AssemblyFileVersion to 1.0.0.99.</span><span class="sxs-lookup"><span data-stu-id="2b96e-152">For example, you are building version 1.0.0 of your project, and the continuous integration build number is 99 so your AssemblyFileVersion is 1.0.0.99.</span></span>

<span data-ttu-id="2b96e-153">**✔️** użyj formatu `Major.Minor.Build.Revision` dla wersji pliku.</span><span class="sxs-lookup"><span data-stu-id="2b96e-153">**✔️ DO** use the format `Major.Minor.Build.Revision` for file version.</span></span>

> <span data-ttu-id="2b96e-154">Mimo że wersja pliku nigdy nie jest używana przez platformę .NET, [system Windows oczekuje, że wersja pliku](/windows/desktop/menurc/versioninfo-resource) będzie w formacie `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="2b96e-154">While the file version is never used by .NET, [Windows expects the file version](/windows/desktop/menurc/versioninfo-resource) to be in the `Major.Minor.Build.Revision` format.</span></span> <span data-ttu-id="2b96e-155">Ostrzeżenie jest zgłaszane, jeśli wersja nie jest zgodna z tym formatem.</span><span class="sxs-lookup"><span data-stu-id="2b96e-155">A warning is raised if the version doesn't follow this format.</span></span>

### <a name="assembly-informational-version"></a><span data-ttu-id="2b96e-156">Informacje o wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="2b96e-156">Assembly informational version</span></span>

<span data-ttu-id="2b96e-157">Informacje o wersji zestawu są używane do rejestrowania dodatkowych informacji o wersji i nie mają wpływu na zachowanie w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2b96e-157">The assembly informational version is used to record additional version information and has no effect on runtime behavior.</span></span> <span data-ttu-id="2b96e-158">Ustawienie tej wersji jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="2b96e-158">Setting this version is optional.</span></span> <span data-ttu-id="2b96e-159">Jeśli używasz linku źródłowego, ta wersja zostanie ustawiona na kompilację z wersją pakietu NuGet i wersją kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="2b96e-159">If you're using Source Link, this version will be set on build with the NuGet package version plus a source control version.</span></span> <span data-ttu-id="2b96e-160">Na przykład `1.0.0-beta1+204ff0a` zawiera skrót zatwierdzenia kodu źródłowego, z którego zestaw został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="2b96e-160">For example, `1.0.0-beta1+204ff0a` includes the commit hash of the source code the assembly was built from.</span></span> <span data-ttu-id="2b96e-161">Aby uzyskać więcej informacji, zobacz [link źródłowy](./sourcelink.md).</span><span class="sxs-lookup"><span data-stu-id="2b96e-161">For more information, see [Source Link](./sourcelink.md).</span></span>

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> <span data-ttu-id="2b96e-162">Starsze wersje programu Visual Studio zgłaszają ostrzeżenie kompilacji, jeśli ta wersja nie jest zgodna z formatem `Major.Minor.Build.Revision`.</span><span class="sxs-lookup"><span data-stu-id="2b96e-162">Older versions of Visual Studio raise a build warning if this version doesn't follow the format `Major.Minor.Build.Revision`.</span></span> <span data-ttu-id="2b96e-163">Ostrzeżenie można bezpiecznie zignorować.</span><span class="sxs-lookup"><span data-stu-id="2b96e-163">The warning can be safely ignored.</span></span>

<span data-ttu-id="2b96e-164">**❌ Nie należy** samodzielnie ustawić wersji informacyjnej zestawu.</span><span class="sxs-lookup"><span data-stu-id="2b96e-164">**❌ AVOID** setting the assembly informational version yourself.</span></span>

> <span data-ttu-id="2b96e-165">Zezwól programowi SourceLink na automatyczne generowanie wersji zawierającej metadane narzędzia NuGet i kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="2b96e-165">Allow SourceLink to automatically generate the version containing NuGet and source control metadata.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2b96e-166">[Poprzedni](publish-nuget-package.md)
>[Następny](breaking-changes.md)</span><span class="sxs-lookup"><span data-stu-id="2b96e-166">[Previous](publish-nuget-package.md)
[Next](breaking-changes.md)</span></span>
