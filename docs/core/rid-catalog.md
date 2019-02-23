---
title: Katalog platformy .NET core środowiska uruchomieniowego identyfikator (RID)
description: Informacje o identyfikator środowiska uruchomieniowego (RID) i jak identyfikatorów RID są używane w programie .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: 0d03e39c755b43e145edf5efe48422cbae7abcab
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745745"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="b0a45-103">.NET core RID katalogu</span><span class="sxs-lookup"><span data-stu-id="b0a45-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="b0a45-104">Identyfikatorów RID jest mała w przypadku *identyfikator środowiska uruchomieniowego*.</span><span class="sxs-lookup"><span data-stu-id="b0a45-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="b0a45-105">RID wartości są używane do identyfikowania platformy docelowe, w którym działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="b0a45-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="b0a45-106">Są używane przez pakiety .NET do reprezentowania zasoby specyficzne dla platformy w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0a45-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="b0a45-107">Przykłady identyfikatorów RID są następujące wartości: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="b0a45-108">W przypadku pakietów zależności natywnych RID wyznacza platformy, na których można przywrócić pakietu.</span><span class="sxs-lookup"><span data-stu-id="b0a45-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="b0a45-109">Pojedynczy RID można ustawić w `<RuntimeIdentifier>` elementu z pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b0a45-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="b0a45-110">Wiele identyfikatorów RID mogą być definiowane jako rozdzielaną średnikami listę w pliku projektu `<RuntimeIdentifiers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b0a45-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="b0a45-111">Są również używane za pośrednictwem `--runtime` opcji z następujących [poleceń interfejsu wiersza polecenia platformy .NET Core](./tools/index.md):</span><span class="sxs-lookup"><span data-stu-id="b0a45-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="b0a45-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="b0a45-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="b0a45-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="b0a45-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="b0a45-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="b0a45-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="b0a45-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="b0a45-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="b0a45-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b0a45-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="b0a45-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="b0a45-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="b0a45-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="b0a45-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="b0a45-119">Identyfikatorów RID, reprezentujące systemy operacyjne konkretnych zwykle skorzystaj z tego wzorca: `[os].[version]-[architecture]-[additional qualifiers]` gdzie:</span><span class="sxs-lookup"><span data-stu-id="b0a45-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="b0a45-120">`[os]` jest krótkiej nazwy systemu operacyjnego i platformy.</span><span class="sxs-lookup"><span data-stu-id="b0a45-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="b0a45-121">Na przykład `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="b0a45-122">`[version]` jest to wersja systemu operacyjnego w formie oddzielone kropką (`.`) numer wersji.</span><span class="sxs-lookup"><span data-stu-id="b0a45-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="b0a45-123">Na przykład `15.10`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="b0a45-124">Wersja **nie powinien** marketingowych w wersjach, jak często reprezentują wielu dyskretnych wersji systemu operacyjnego ze zróżnicowanymi obszar powierzchni interfejsu API platformy.</span><span class="sxs-lookup"><span data-stu-id="b0a45-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="b0a45-125">`[architecture]` jest to architektura procesora.</span><span class="sxs-lookup"><span data-stu-id="b0a45-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="b0a45-126">Na przykład: `x86`, `x64`, `arm`, lub `arm64`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="b0a45-127">`[additional qualifiers]` możliwości rozróżniania różnych platformach.</span><span class="sxs-lookup"><span data-stu-id="b0a45-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="b0a45-128">Na przykład: `aot`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="b0a45-129">Wykres RID</span><span class="sxs-lookup"><span data-stu-id="b0a45-129">RID graph</span></span>

<span data-ttu-id="b0a45-130">RID wykresu lub grafu rezerwowego środowisko uruchomieniowe znajduje się lista identyfikatorów RID, które są ze sobą zgodne.</span><span class="sxs-lookup"><span data-stu-id="b0a45-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="b0a45-131">Identyfikatorów RID są zdefiniowane w [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) pakietu.</span><span class="sxs-lookup"><span data-stu-id="b0a45-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="b0a45-132">Można wyświetlić listę obsługiwanych identyfikatorów RID i wykres RID [ *runtime.json* ](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku, który znajduje się w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="b0a45-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the CoreFX repo.</span></span> <span data-ttu-id="b0a45-133">W tym pliku widać, że wszystkich identyfikatorów RID, z wyjątkiem dla nich podstawowy zawiera `"#import"` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b0a45-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="b0a45-134">Te instrukcje wskazują zgodnych identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="b0a45-135">Gdy NuGet przywraca pakietów, próbuje odnaleźć dokładnego dopasowania dla określonego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b0a45-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="b0a45-136">Jeśli nie zostanie znalezione dokładne dopasowanie, NuGet przedstawia powrót wykresu do momentu znalezienia najbliższego zgodny system zgodnie z wykresu identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="b0a45-137">Poniższy przykład jest to rzeczywiste zapis `osx.10.12-x64` identyfikatorów RID:</span><span class="sxs-lookup"><span data-stu-id="b0a45-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="b0a45-138">Powyższe RID Określa, że `osx.10.12-x64` importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="b0a45-139">Tak, gdy NuGet przywraca pakietów, próbuje odnaleźć dokładnego dopasowania dla `osx.10.12-x64` w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="b0a45-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="b0a45-140">Jeśli NuGet nie może odnaleźć określonego środowiska uruchomieniowego, przywracanie pakietów, które określają `osx.10.11-x64` środowisk wykonawczych, na przykład.</span><span class="sxs-lookup"><span data-stu-id="b0a45-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="b0a45-141">W poniższym przykładzie przedstawiono wykres RID nieco większy, również zdefiniowanej w *runtime.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="b0a45-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="b0a45-142">Wszystkich identyfikatorów RID po pewnym czasie zamapować powrót do katalogu głównego `any` identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="b0a45-143">Istnieją pewne zagadnienia dotyczące identyfikatorów RID, które trzeba mieć na uwadze podczas pracy z nimi:</span><span class="sxs-lookup"><span data-stu-id="b0a45-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="b0a45-144">Identyfikatorów RID są **nieprzezroczyste ciągi** i powinny być traktowane jako pola czarny.</span><span class="sxs-lookup"><span data-stu-id="b0a45-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="b0a45-145">Nie twórz programowo identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="b0a45-146">Użyj identyfikatorów RID, które są już zdefiniowane dla platformy.</span><span class="sxs-lookup"><span data-stu-id="b0a45-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="b0a45-147">RID muszą być określone, dzięki czemu nie wolno zakładać cokolwiek — od rzeczywistej wartości identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="b0a45-148">Przy użyciu identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="b0a45-148">Using RIDs</span></span>

<span data-ttu-id="b0a45-149">Aby można było używać identyfikatorów RID, musisz wiedzieć, który istnieje identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="b0a45-150">Nowe wartości są regularnie dodawane do korzystania z platformy.</span><span class="sxs-lookup"><span data-stu-id="b0a45-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="b0a45-151">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="b0a45-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

<span data-ttu-id="b0a45-152">.NET core 2.0 SDK wprowadzono pojęcie przenośne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="b0a45-153">Są one nowe wartości dodane do grafu identyfikatorów RID, które nie są powiązane z konkretną wersję lub dystrybucji systemu operacyjnego i są preferowanych przez, korzystając z platformy .NET Core 2.0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="b0a45-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="b0a45-154">Są one szczególnie użyteczne w przypadku, gdy zajmowanie wielu dystrybucje systemu Linux, ponieważ większość RID dystrybucji są mapowane na przenośnym identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="b0a45-155">Na poniższej liście przedstawiono małego podzbioru typowych identyfikatorów RID, używane dla każdego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b0a45-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="b0a45-156">Windows identyfikatorów RID</span><span class="sxs-lookup"><span data-stu-id="b0a45-156">Windows RIDs</span></span>

<span data-ttu-id="b0a45-157">Tylko wartości typowych są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b0a45-157">Only common values are listed.</span></span> <span data-ttu-id="b0a45-158">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="b0a45-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="b0a45-159">Przenośna (.NET Core 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="b0a45-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="b0a45-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="b0a45-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="b0a45-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="b0a45-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="b0a45-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="b0a45-163">Zobacz [wymagania wstępne dla platformy .NET Core w Windows](windows-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b0a45-163">See [Prerequisites for .NET Core on Windows](windows-prerequisites.md) for more information.</span></span>

## <a name="linux-rids"></a><span data-ttu-id="b0a45-164">Identyfikatorów RID w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="b0a45-164">Linux RIDs</span></span>

<span data-ttu-id="b0a45-165">Tylko wartości typowych są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b0a45-165">Only common values are listed.</span></span> <span data-ttu-id="b0a45-166">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="b0a45-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span> <span data-ttu-id="b0a45-167">Urządzenia z systemem dystrybucji nie są wymienione poniżej mogą działać z jedną przenośne identyfikatorów RID.</span><span class="sxs-lookup"><span data-stu-id="b0a45-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="b0a45-168">Na przykład, można zastosować urządzenia Raspberry Pi korzystania z dystrybucji systemu Linux, niewymienionych `linux-arm`.</span><span class="sxs-lookup"><span data-stu-id="b0a45-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="b0a45-169">Przenośna (.NET Core 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="b0a45-170">`linux-x64` (Większość dystrybucje pulpitu, takie jak CentOS, Debian, Fedora, Ubuntu i ich pochodnych)</span><span class="sxs-lookup"><span data-stu-id="b0a45-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu and derivatives)</span></span>
  - <span data-ttu-id="b0a45-171">`linux-musl-x64` (Dystrybucje lightweight przy użyciu [musl](https://wiki.musl-libc.org/projects-using-musl.html) Alpine Linux, takie jak)</span><span class="sxs-lookup"><span data-stu-id="b0a45-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="b0a45-172">`linux-arm` (Dystrybucje systemu Linux w systemie ARM, takich jak Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="b0a45-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="b0a45-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="b0a45-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="b0a45-174">`rhel-x64` (Zastąpiona `linux-x64` systemu RHEL powyżej w wersji 6)</span><span class="sxs-lookup"><span data-stu-id="b0a45-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="b0a45-175">`rhel.6-x64` (.NET core 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="b0a45-176">Tizen (.NET Core 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="b0a45-177">Zobacz [wymagania wstępne dla platformy .NET Core w systemie Linux](linux-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b0a45-177">See [Prerequisites for .NET Core on Linux](linux-prerequisites.md) for more information.</span></span>

## <a name="macos-rids"></a><span data-ttu-id="b0a45-178">RID z systemem macOS</span><span class="sxs-lookup"><span data-stu-id="b0a45-178">macOS RIDs</span></span>

<span data-ttu-id="b0a45-179">RID z systemem macOS za pomocą starszej znakowania "OSX".</span><span class="sxs-lookup"><span data-stu-id="b0a45-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="b0a45-180">Tylko wartości typowych są wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="b0a45-180">Only common values are listed.</span></span> <span data-ttu-id="b0a45-181">Najnowsze i pełna wersja dla [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) pliku w repozytorium CoreFX.</span><span class="sxs-lookup"><span data-stu-id="b0a45-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

- <span data-ttu-id="b0a45-182">Przenośna (.NET Core 2.0 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="b0a45-183">`osx-x64` (Minimalna wersja systemu operacyjnego jest macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="b0a45-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="b0a45-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="b0a45-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="b0a45-185">System macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="b0a45-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="b0a45-186">System macOS 10.12 Sierra (.NET Core 1.1 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="b0a45-187">macOS 10.13 High Sierra (.NET Core 1.1 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="b0a45-188">System macOS 10.14 Mojave (.NET Core 1.1 lub nowszy)</span><span class="sxs-lookup"><span data-stu-id="b0a45-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="b0a45-189">Zobacz [wymagania wstępne dla platformy .NET Core w systemie macOS](macos-prerequisites.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="b0a45-189">See [Prerequisites for .NET Core on macOS](macos-prerequisites.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0a45-190">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0a45-190">See also</span></span>

- [<span data-ttu-id="b0a45-191">Identyfikatory środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="b0a45-191">Runtime IDs</span></span>](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/readme.md)
