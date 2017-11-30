---
title: "Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)"
description: "Więcej informacji na temat identyfikatora środowiska uruchomieniowego (RID) i używania identyfikatorów RID w .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 067f9cfc283a14b7ea59a7454b7f593ce6eb5806
ms.sourcegitcommit: 62d3e3e74c1b7ffa927590012c0b9f87de1b0848
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="004e3-103">.NET core RID katalogu</span><span class="sxs-lookup"><span data-stu-id="004e3-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="004e3-104">Identyfikatorów RID jest skrót *identyfikator środowiska uruchomieniowego*.</span><span class="sxs-lookup"><span data-stu-id="004e3-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="004e3-105">Wartości identyfikatorów RID są używane do identyfikacji platform docelowych, którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="004e3-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="004e3-106">Są one używane przez pakiety .NET do reprezentowania zasoby specyficzne dla platformy w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="004e3-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="004e3-107">Przykłady identyfikatorów RID są następujące wartości: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="004e3-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="004e3-108">Pakietów z zależnościami natywnego RID wyznacza platformy, na których można przywrócić pakietu.</span><span class="sxs-lookup"><span data-stu-id="004e3-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="004e3-109">Można ustawić identyfikatorów RID w `<RuntimeIdentifier>` element pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="004e3-109">RIDs can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="004e3-110">Są również używane za pośrednictwem `--runtime` opcji z następującymi [polecenia interfejsu wiersza polecenia platformy .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="004e3-110">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="004e3-111">Kompilacja DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-111">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="004e3-112">Wyczyść DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-112">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="004e3-113">Pakiet DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-113">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="004e3-114">Publikowanie DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-114">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="004e3-115">Przywracanie DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-115">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="004e3-116">Uruchom DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-116">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="004e3-117">Magazyn DotNet</span><span class="sxs-lookup"><span data-stu-id="004e3-117">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="004e3-118">Identyfikatorów RID, reprezentują konkretnych systemów operacyjnych zwykle skorzystaj z tego wzorca: `[os].[version]-[architecture]-[additional qualifiers]` gdzie:</span><span class="sxs-lookup"><span data-stu-id="004e3-118">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="004e3-119">`[os]`jest krótkiej nazwy systemu operacyjnego platformy.</span><span class="sxs-lookup"><span data-stu-id="004e3-119">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="004e3-120">Na przykład `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="004e3-120">For example, `ubuntu`.</span></span>

- <span data-ttu-id="004e3-121">`[version]`jest to wersja systemu operacyjnego w formie oddzielona kropkami (`.`) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="004e3-121">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="004e3-122">Na przykład `15.10`.</span><span class="sxs-lookup"><span data-stu-id="004e3-122">For example, `15.10`.</span></span>

  - <span data-ttu-id="004e3-123">Wersja **nie powinny** marketingowe w wersji, ponieważ stanowią one często wielu odrębny wersji systemu operacyjnego ze zróżnicowanymi powierzchni interfejsu API platformy.</span><span class="sxs-lookup"><span data-stu-id="004e3-123">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="004e3-124">`[architecture]`to architektura procesora.</span><span class="sxs-lookup"><span data-stu-id="004e3-124">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="004e3-125">Na przykład: `x86`, `x64`, `arm`, lub `arm64`.</span><span class="sxs-lookup"><span data-stu-id="004e3-125">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="004e3-126">`[additional qualifiers]`rozróżniania różnych platform.</span><span class="sxs-lookup"><span data-stu-id="004e3-126">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="004e3-127">Na przykład: `aot` lub `corert`.</span><span class="sxs-lookup"><span data-stu-id="004e3-127">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="004e3-128">Wykres identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="004e3-128">RID graph</span></span>

<span data-ttu-id="004e3-129">Wykres identyfikatorów RID lub wykres rezerwowy środowiska uruchomieniowego znajduje się lista identyfikatorów RID, które są zgodne ze sobą.</span><span class="sxs-lookup"><span data-stu-id="004e3-129">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="004e3-130">Identyfikatorów RID są zdefiniowane w [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) pakietu.</span><span class="sxs-lookup"><span data-stu-id="004e3-130">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="004e3-131">Można wyświetlić listę obsługiwanych identyfikatorów RID i wykres identyfikatorów RID w [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku, który znajduje się w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="004e3-131">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="004e3-132">W tym pliku widać, że wszystkie identyfikatorów RID, z wyjątkiem podstawowego katalogu zawiera `"#import"` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="004e3-132">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="004e3-133">Te instrukcje wskazują zgodne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-133">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="004e3-134">Gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla określonego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="004e3-134">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="004e3-135">Jeśli nie znaleziono dokładnego dopasowania, NuGet przeprowadzi Cię wstecz wykresu aż do znalezienia najbliższego zgodny system zgodnie z wykresu identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-135">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="004e3-136">Poniższy przykład jest to rzeczywiste zapis `osx.10.12-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="004e3-136">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="004e3-137">Powyżej RID Określa, że `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="004e3-137">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="004e3-138">Tak, gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla `osx.10.12-x64` w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="004e3-138">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="004e3-139">Jeśli NuGet nie może znaleźć określonego środowiska uruchomieniowego, można przywrócić pakiety, które określają `osx.10.11-x64` środowisk uruchomieniowych, na przykład.</span><span class="sxs-lookup"><span data-stu-id="004e3-139">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="004e3-140">W poniższym przykładzie przedstawiono nieco większy wykres RID też definiowany w *runtime.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="004e3-140">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

```
    win7-x64    win7-x86
       |   \   /    |
       |   win7     |
       |     |      |
    win-x64  |  win-x86
          \  |  /
            win
             |
            any
```

<span data-ttu-id="004e3-141">Wszystkie identyfikatorów RID po pewnym czasie mapy od głównego `any` identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-141">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="004e3-142">Istnieje kilka dodatkowych kwestii dotyczących identyfikatorów RID, które należy mieć na uwadze podczas pracy z nimi:</span><span class="sxs-lookup"><span data-stu-id="004e3-142">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="004e3-143">Identyfikatorów RID są **nieprzezroczyste ciągów** i powinien być traktowany jako czarne pola.</span><span class="sxs-lookup"><span data-stu-id="004e3-143">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="004e3-144">Nie Konstruuj programowo identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-144">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="004e3-145">Użyj identyfikatorów RID, które zostały już zdefiniowane dla platformy.</span><span class="sxs-lookup"><span data-stu-id="004e3-145">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="004e3-146">RID muszą być określone, więc nie wolno zakładać nic rzeczywistej wartości identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-146">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="004e3-147">Przy użyciu identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="004e3-147">Using RIDs</span></span>

<span data-ttu-id="004e3-148">Aby można było użyć identyfikatorów RID, trzeba znać istniejących identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-148">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="004e3-149">Regularnie dodawane nowe wartości dla platformy.</span><span class="sxs-lookup"><span data-stu-id="004e3-149">New values are added regularly to the platform.</span></span>
<span data-ttu-id="004e3-150">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku na CoreFX repozytorium.</span><span class="sxs-lookup"><span data-stu-id="004e3-150">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="004e3-151">.NET core 2.0 SDK wprowadza pojęcia przenośne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="004e3-151">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="004e3-152">Są one nowe wartości dodawać do wykresu identyfikatorów RID, które nie są powiązane określonej wersji lub dystrybucji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="004e3-152">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="004e3-153">Są one szczególnie użyteczne w przypadku wielu dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="004e3-153">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="004e3-154">Poniższa lista przedstawia najbardziej typowe identyfikatorów RID używane dla każdego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="004e3-154">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="004e3-155">Nie obejmuje ona `arm` lub `corert` wartości.</span><span class="sxs-lookup"><span data-stu-id="004e3-155">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="004e3-156">RID systemu Windows</span><span class="sxs-lookup"><span data-stu-id="004e3-156">Windows RIDs</span></span>

- <span data-ttu-id="004e3-157">Przenośna</span><span class="sxs-lookup"><span data-stu-id="004e3-157">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="004e3-158">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="004e3-158">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="004e3-159">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="004e3-159">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="004e3-160">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="004e3-160">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="004e3-161">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="004e3-161">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="004e3-162">Zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](windows-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="004e3-162">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="004e3-163">Linux identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="004e3-163">Linux RIDs</span></span>

- <span data-ttu-id="004e3-164">Przenośna</span><span class="sxs-lookup"><span data-stu-id="004e3-164">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="004e3-165">CentOS</span><span class="sxs-lookup"><span data-stu-id="004e3-165">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="004e3-166">Debian</span><span class="sxs-lookup"><span data-stu-id="004e3-166">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="004e3-167">Fedora</span><span class="sxs-lookup"><span data-stu-id="004e3-167">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="004e3-168">`fedora.25-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-168">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="004e3-169">`fedora.26-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-169">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="004e3-170">Gentoo (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-170">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="004e3-171">openSUSE</span><span class="sxs-lookup"><span data-stu-id="004e3-171">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="004e3-172">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="004e3-172">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="004e3-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="004e3-173">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="004e3-174">`rhel.6-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-174">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="004e3-175">`rhel.7.3-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-175">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="004e3-176">`rhel.7.4-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-176">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="004e3-177">Tizen (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-177">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="004e3-178">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="004e3-178">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="004e3-179">Ubuntu pochodne</span><span class="sxs-lookup"><span data-stu-id="004e3-179">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="004e3-180">`linuxmint.18.1-x64`(.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-180">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="004e3-181">Zobacz [wymagania wstępne dotyczące .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="004e3-181">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="004e3-182">System macOS identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="004e3-182">macOS RIDs</span></span>

<span data-ttu-id="004e3-183">System macOS RID za pomocą starszej znakowania "OS x".</span><span class="sxs-lookup"><span data-stu-id="004e3-183">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="004e3-184">`osx-x64`(.NET core w wersji 2.0 lub nowszy, minimalna wersja to `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="004e3-184">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="004e3-185">`osx.10.12-x64`(.NET core 1.1 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-185">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="004e3-186">Zobacz [wymagania wstępne dotyczące .NET Core na macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="004e3-186">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="004e3-187">Android identyfikatorów RID (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="004e3-187">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="004e3-188">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="004e3-188">See also</span></span>

[<span data-ttu-id="004e3-189">Identyfikatory środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="004e3-189">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
