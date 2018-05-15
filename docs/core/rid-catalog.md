---
title: Katalogu .NET core środowiska uruchomieniowego identyfikator (RID)
description: Więcej informacji na temat identyfikatora środowiska uruchomieniowego (RID) i używania identyfikatorów RID w .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 09/07/2017
ms.openlocfilehash: 81f9e5f65385bbd81c7fdae7f75c62d11b6f6319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="70160-103">.NET core RID katalogu</span><span class="sxs-lookup"><span data-stu-id="70160-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="70160-104">Identyfikatorów RID jest skrót *identyfikator środowiska uruchomieniowego*.</span><span class="sxs-lookup"><span data-stu-id="70160-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="70160-105">Wartości identyfikatorów RID są używane do identyfikacji platform docelowych, którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="70160-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="70160-106">Są one używane przez pakiety .NET do reprezentowania zasoby specyficzne dla platformy w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="70160-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="70160-107">Przykłady identyfikatorów RID są następujące wartości: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="70160-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="70160-108">Pakietów z zależnościami natywnego RID wyznacza platformy, na których można przywrócić pakietu.</span><span class="sxs-lookup"><span data-stu-id="70160-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="70160-109">Pojedynczy RID można ustawić w `<RuntimeIdentifier>` element pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="70160-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="70160-110">Wiele identyfikatorów RID może być zdefiniowana jako listę rozdzielaną średnikami w pliku projektu `<RuntimeIdentifiers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="70160-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="70160-111">Są również używane za pośrednictwem `--runtime` opcji z następującymi [polecenia interfejsu wiersza polecenia platformy .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="70160-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="70160-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="70160-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="70160-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="70160-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="70160-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="70160-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="70160-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="70160-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="70160-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="70160-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="70160-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="70160-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="70160-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="70160-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="70160-119">Identyfikatorów RID, reprezentują konkretnych systemów operacyjnych zwykle skorzystaj z tego wzorca: `[os].[version]-[architecture]-[additional qualifiers]` gdzie:</span><span class="sxs-lookup"><span data-stu-id="70160-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="70160-120">`[os]` jest krótkiej nazwy systemu operacyjnego platformy.</span><span class="sxs-lookup"><span data-stu-id="70160-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="70160-121">Na przykład `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="70160-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="70160-122">`[version]` jest to wersja systemu operacyjnego w formie oddzielona kropkami (`.`) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="70160-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="70160-123">Na przykład `15.10`.</span><span class="sxs-lookup"><span data-stu-id="70160-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="70160-124">Wersja **nie powinny** marketingowe w wersji, ponieważ stanowią one często wielu odrębny wersji systemu operacyjnego ze zróżnicowanymi powierzchni interfejsu API platformy.</span><span class="sxs-lookup"><span data-stu-id="70160-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="70160-125">`[architecture]` to architektura procesora.</span><span class="sxs-lookup"><span data-stu-id="70160-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="70160-126">Na przykład: `x86`, `x64`, `arm`, lub `arm64`.</span><span class="sxs-lookup"><span data-stu-id="70160-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="70160-127">`[additional qualifiers]` rozróżniania różnych platform.</span><span class="sxs-lookup"><span data-stu-id="70160-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="70160-128">Na przykład: `aot` lub `corert`.</span><span class="sxs-lookup"><span data-stu-id="70160-128">For example: `aot` or `corert`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="70160-129">Wykres identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="70160-129">RID graph</span></span>

<span data-ttu-id="70160-130">Wykres identyfikatorów RID lub wykres rezerwowy środowiska uruchomieniowego znajduje się lista identyfikatorów RID, które są zgodne ze sobą.</span><span class="sxs-lookup"><span data-stu-id="70160-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="70160-131">Identyfikatorów RID są zdefiniowane w [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) pakietu.</span><span class="sxs-lookup"><span data-stu-id="70160-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="70160-132">Można wyświetlić listę obsługiwanych identyfikatorów RID i wykres identyfikatorów RID w [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku, który znajduje się w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="70160-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="70160-133">W tym pliku widać, że wszystkie identyfikatorów RID, z wyjątkiem podstawowego katalogu zawiera `"#import"` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="70160-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="70160-134">Te instrukcje wskazują zgodne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="70160-135">Gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla określonego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="70160-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="70160-136">Jeśli nie znaleziono dokładnego dopasowania, NuGet przeprowadzi Cię wstecz wykresu aż do znalezienia najbliższego zgodny system zgodnie z wykresu identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="70160-137">Poniższy przykład jest to rzeczywiste zapis `osx.10.12-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="70160-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="70160-138">Powyżej RID Określa, że `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="70160-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="70160-139">Tak, gdy NuGet przywraca pakietów, próbuje znaleźć dokładnego dopasowania dla `osx.10.12-x64` w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="70160-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="70160-140">Jeśli NuGet nie może znaleźć określonego środowiska uruchomieniowego, można przywrócić pakiety, które określają `osx.10.11-x64` środowisk uruchomieniowych, na przykład.</span><span class="sxs-lookup"><span data-stu-id="70160-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="70160-141">W poniższym przykładzie przedstawiono nieco większy wykres RID też definiowany w *runtime.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="70160-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="70160-142">Wszystkie identyfikatorów RID po pewnym czasie mapy od głównego `any` identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="70160-143">Istnieje kilka dodatkowych kwestii dotyczących identyfikatorów RID, które należy mieć na uwadze podczas pracy z nimi:</span><span class="sxs-lookup"><span data-stu-id="70160-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="70160-144">Identyfikatorów RID są **nieprzezroczyste ciągów** i powinien być traktowany jako czarne pola.</span><span class="sxs-lookup"><span data-stu-id="70160-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="70160-145">Nie Konstruuj programowo identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="70160-146">Użyj identyfikatorów RID, które zostały już zdefiniowane dla platformy.</span><span class="sxs-lookup"><span data-stu-id="70160-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="70160-147">RID muszą być określone, więc nie wolno zakładać nic rzeczywistej wartości identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="70160-148">Przy użyciu identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="70160-148">Using RIDs</span></span>

<span data-ttu-id="70160-149">Aby można było użyć identyfikatorów RID, trzeba znać istniejących identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="70160-150">Regularnie dodawane nowe wartości dla platformy.</span><span class="sxs-lookup"><span data-stu-id="70160-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="70160-151">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku na CoreFX repozytorium.</span><span class="sxs-lookup"><span data-stu-id="70160-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="70160-152">.NET core 2.0 SDK wprowadza pojęcia przenośne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="70160-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="70160-153">Są one nowe wartości dodawać do wykresu identyfikatorów RID, które nie są powiązane określonej wersji lub dystrybucji systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="70160-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution.</span></span> <span data-ttu-id="70160-154">Są one szczególnie użyteczne w przypadku wielu dystrybucjach systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="70160-154">They're particularly useful when dealing with multiple Linux distros.</span></span>

<span data-ttu-id="70160-155">Poniższa lista przedstawia najbardziej typowe identyfikatorów RID używane dla każdego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="70160-155">The following list shows the most common RIDs used for each OS.</span></span> <span data-ttu-id="70160-156">Nie obejmuje ona `arm` lub `corert` wartości.</span><span class="sxs-lookup"><span data-stu-id="70160-156">It doesn't cover `arm` or `corert` values.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="70160-157">RID systemu Windows</span><span class="sxs-lookup"><span data-stu-id="70160-157">Windows RIDs</span></span>

- <span data-ttu-id="70160-158">Przenośna</span><span class="sxs-lookup"><span data-stu-id="70160-158">Portable</span></span>
  - `win-x86`
  - `win-x64`
- <span data-ttu-id="70160-159">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="70160-159">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="70160-160">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="70160-160">Windows 8 / Windows Server 2012</span></span>
  - `win8-x64`
  - `win8-x86`
  - `win8-arm`
- <span data-ttu-id="70160-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="70160-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="70160-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="70160-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="70160-163">Zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](windows-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="70160-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="70160-164">Linux identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="70160-164">Linux RIDs</span></span>

- <span data-ttu-id="70160-165">Przenośna</span><span class="sxs-lookup"><span data-stu-id="70160-165">Portable</span></span>
  - `linux-x64`
- <span data-ttu-id="70160-166">CentOS</span><span class="sxs-lookup"><span data-stu-id="70160-166">CentOS</span></span>
  - `centos-x64`
  - `centos.7-x64`
- <span data-ttu-id="70160-167">Debian</span><span class="sxs-lookup"><span data-stu-id="70160-167">Debian</span></span>
  - `debian-x64`
  - `debian.8-x64`
- <span data-ttu-id="70160-168">Fedora</span><span class="sxs-lookup"><span data-stu-id="70160-168">Fedora</span></span>
  - `fedora-x64`
  - `fedora.24-x64`
  - <span data-ttu-id="70160-169">`fedora.25-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-169">`fedora.25-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="70160-170">`fedora.26-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-170">`fedora.26-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="70160-171">Gentoo (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-171">Gentoo (.NET Core 2.0 or later versions)</span></span>
  - `gentoo-x64`
- <span data-ttu-id="70160-172">openSUSE</span><span class="sxs-lookup"><span data-stu-id="70160-172">openSUSE</span></span>
  - `opensuse-x64`
  - `opensuse.42.1-x64`
- <span data-ttu-id="70160-173">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="70160-173">Oracle Linux</span></span>
  - `ol-x64`
  - `ol.7-x64`
  - `ol.7.0-x64`
  - `ol.7.1-x64`
  - `ol.7.2-x64`
- <span data-ttu-id="70160-174">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="70160-174">Red Hat Enterprise Linux</span></span>
  - `rhel-x64`
  - <span data-ttu-id="70160-175">`rhel.6-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
  - `rhel.7-x64`
  - `rhel.7.1-x64`
  - `rhel.7.2-x64`
  - <span data-ttu-id="70160-176">`rhel.7.3-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-176">`rhel.7.3-x64` (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="70160-177">`rhel.7.4-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-177">`rhel.7.4-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="70160-178">Tizen (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-178">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
- <span data-ttu-id="70160-179">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="70160-179">Ubuntu</span></span>
  - `ubuntu-x64`
  - `ubuntu.14.04-x64`
  - `ubuntu.14.10-x64`
  - `ubuntu.15.04-x64`
  - `ubuntu.15.10-x64`
  - `ubuntu.16.04-x64`
  - `ubuntu.16.10-x64`
- <span data-ttu-id="70160-180">Ubuntu pochodne</span><span class="sxs-lookup"><span data-stu-id="70160-180">Ubuntu derivatives</span></span>
  - `linuxmint.17-x64`
  - `linuxmint.17.1-x64`
  - `linuxmint.17.2-x64`
  - `linuxmint.17.3-x64`
  - `linuxmint.18-x64`
  - <span data-ttu-id="70160-181">`linuxmint.18.1-x64` (.NET core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-181">`linuxmint.18.1-x64` (.NET Core 2.0 or later versions)</span></span>

<span data-ttu-id="70160-182">Zobacz [wymagania wstępne dotyczące .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="70160-182">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="70160-183">System macOS identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="70160-183">macOS RIDs</span></span>

<span data-ttu-id="70160-184">System macOS RID za pomocą starszej znakowania "OS x".</span><span class="sxs-lookup"><span data-stu-id="70160-184">macOS RIDs use the older "OSX" branding.</span></span>

- <span data-ttu-id="70160-185">`osx-x64` (.NET core w wersji 2.0 lub nowszy, minimalna wersja to `osx.10.12-x64`)</span><span class="sxs-lookup"><span data-stu-id="70160-185">`osx-x64` (.NET Core 2.0 or later versions, minimum version is `osx.10.12-x64`)</span></span>
- `osx.10.10-x64`
- `osx.10.11-x64`
- <span data-ttu-id="70160-186">`osx.10.12-x64` (.NET core 1.1 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-186">`osx.10.12-x64` (.NET Core 1.1 or later versions)</span></span>
- `osx.10.13-x64`

<span data-ttu-id="70160-187">Zobacz [wymagania wstępne dotyczące .NET Core na macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="70160-187">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="android-rids-net-core-20-or-later-versions"></a><span data-ttu-id="70160-188">Android identyfikatorów RID (.NET Core w wersji 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="70160-188">Android RIDs (.NET Core 2.0 or later versions)</span></span>

- `android`
- `android.21`

## <a name="see-also"></a><span data-ttu-id="70160-189">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70160-189">See also</span></span>

[<span data-ttu-id="70160-190">Identyfikatory środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="70160-190">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
