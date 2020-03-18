---
title: Wykaz identyfikatora środowiska uruchomienionowego programu .NET Core (RID)
description: Dowiedz się więcej o identyfikatorze IDentifier (RID) i sposobie użycia identyfikatorów RID w ustonach .NET Core.
ms.date: 02/22/2019
ms.openlocfilehash: feb19632f16a047ecfb2dcb697a9b837824a1929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451736"
---
# <a name="net-core-rid-catalog"></a><span data-ttu-id="89052-103">Katalog RID rdzenia .NET</span><span class="sxs-lookup"><span data-stu-id="89052-103">.NET Core RID Catalog</span></span>

<span data-ttu-id="89052-104">Rid jest skrótem od *IDentifier runtime*.</span><span class="sxs-lookup"><span data-stu-id="89052-104">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="89052-105">Wartości RID są używane do identyfikowania platform docelowych, na których działa aplikacja.</span><span class="sxs-lookup"><span data-stu-id="89052-105">RID values are used to identify target platforms where the application runs.</span></span>
<span data-ttu-id="89052-106">Są one używane przez pakiety .NET do reprezentowania zasobów specyficznych dla platformy w pakietach NuGet.</span><span class="sxs-lookup"><span data-stu-id="89052-106">They're used by .NET packages to represent platform-specific assets in NuGet packages.</span></span> <span data-ttu-id="89052-107">Następujące wartości są przykładami identyfikatorów `linux-x64`IDENTYFIKATORÓW: , `ubuntu.14.04-x64`, `win7-x64`, lub `osx.10.12-x64`.</span><span class="sxs-lookup"><span data-stu-id="89052-107">The following values are examples of RIDs: `linux-x64`, `ubuntu.14.04-x64`, `win7-x64`, or `osx.10.12-x64`.</span></span>
<span data-ttu-id="89052-108">W przypadku pakietów z zależnościami macierzystymi rid wyznacza, na których platformach pakiet może zostać przywrócony.</span><span class="sxs-lookup"><span data-stu-id="89052-108">For the packages with native dependencies, the RID designates on which platforms the package can be restored.</span></span>

<span data-ttu-id="89052-109">Pojedynczy identyfikator RID można `<RuntimeIdentifier>` ustawić w elemencie pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="89052-109">A single RID can be set in the `<RuntimeIdentifier>` element of your project file.</span></span> <span data-ttu-id="89052-110">Wiele identyfikatorów IDENTYFIKATORÓW MOŻNA zdefiniować jako listę rozdzielaną średnikami `<RuntimeIdentifiers>` w elemencie pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="89052-110">Multiple RIDs can be defined as a semicolon-delimited list in the project file's `<RuntimeIdentifiers>` element.</span></span> <span data-ttu-id="89052-111">Są one również używane `--runtime` za pomocą opcji z [następującymi poleceniami .NET Core CLI:](./tools/index.md)</span><span class="sxs-lookup"><span data-stu-id="89052-111">They're also used via the `--runtime` option with the following [.NET Core CLI commands](./tools/index.md):</span></span>

- [<span data-ttu-id="89052-112">dotnet build</span><span class="sxs-lookup"><span data-stu-id="89052-112">dotnet build</span></span>](./tools/dotnet-build.md)
- [<span data-ttu-id="89052-113">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="89052-113">dotnet clean</span></span>](./tools/dotnet-clean.md)
- [<span data-ttu-id="89052-114">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="89052-114">dotnet pack</span></span>](./tools/dotnet-pack.md)
- [<span data-ttu-id="89052-115">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="89052-115">dotnet publish</span></span>](./tools/dotnet-publish.md)
- [<span data-ttu-id="89052-116">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="89052-116">dotnet restore</span></span>](./tools/dotnet-restore.md)
- [<span data-ttu-id="89052-117">dotnet run</span><span class="sxs-lookup"><span data-stu-id="89052-117">dotnet run</span></span>](./tools/dotnet-run.md)
- [<span data-ttu-id="89052-118">dotnet store</span><span class="sxs-lookup"><span data-stu-id="89052-118">dotnet store</span></span>](./tools/dotnet-store.md)

<span data-ttu-id="89052-119">IDENTYFIKATORY RID, które reprezentują konkretne systemy `[os].[version]-[architecture]-[additional qualifiers]` operacyjne, zwykle następują po tym wzorze: gdzie:</span><span class="sxs-lookup"><span data-stu-id="89052-119">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[architecture]-[additional qualifiers]` where:</span></span>

- <span data-ttu-id="89052-120">`[os]`jest monikersystemu operacyjnego/platformowego.</span><span class="sxs-lookup"><span data-stu-id="89052-120">`[os]` is the operating/platform system moniker.</span></span> <span data-ttu-id="89052-121">Na przykład `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="89052-121">For example, `ubuntu`.</span></span>

- <span data-ttu-id="89052-122">`[version]`to wersja systemu operacyjnego w postaci numeru wersji`.`oddzielonej kropką ( ) numerwersji.</span><span class="sxs-lookup"><span data-stu-id="89052-122">`[version]` is the operating system version in the form of a dot-separated (`.`) version number.</span></span> <span data-ttu-id="89052-123">Na przykład `15.10`.</span><span class="sxs-lookup"><span data-stu-id="89052-123">For example, `15.10`.</span></span>

  - <span data-ttu-id="89052-124">Wersja **nie powinna** być wersjami marketingowymi, ponieważ często reprezentują one wiele dyskretnych wersji systemu operacyjnego o różnej powierzchni interfejsu API platformy.</span><span class="sxs-lookup"><span data-stu-id="89052-124">The version **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>

- <span data-ttu-id="89052-125">`[architecture]`jest architektura procesora.</span><span class="sxs-lookup"><span data-stu-id="89052-125">`[architecture]` is the processor architecture.</span></span> <span data-ttu-id="89052-126">Na `x86`przykład: `x64` `arm`, `arm64`, , lub .</span><span class="sxs-lookup"><span data-stu-id="89052-126">For example: `x86`, `x64`, `arm`, or `arm64`.</span></span>

- <span data-ttu-id="89052-127">`[additional qualifiers]`dalsze zróżnicowanie różnych platform.</span><span class="sxs-lookup"><span data-stu-id="89052-127">`[additional qualifiers]` further differentiate different platforms.</span></span> <span data-ttu-id="89052-128">Na przykład: `aot`.</span><span class="sxs-lookup"><span data-stu-id="89052-128">For example: `aot`.</span></span>

## <a name="rid-graph"></a><span data-ttu-id="89052-129">Wykres RID</span><span class="sxs-lookup"><span data-stu-id="89052-129">RID graph</span></span>

<span data-ttu-id="89052-130">Wykres RID lub wykres rezerwowy środowiska uruchomieniowego to lista identyfikatorów RID, które są ze sobą zgodne.</span><span class="sxs-lookup"><span data-stu-id="89052-130">The RID graph or runtime fallback graph is a list of RIDs that are compatible with each other.</span></span> <span data-ttu-id="89052-131">Identyfikatory IDENTYFIKATORY są zdefiniowane w pakiecie [Microsoft.NETCore.Platforms.](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/)</span><span class="sxs-lookup"><span data-stu-id="89052-131">The RIDs are defined in the [Microsoft.NETCore.Platforms](https://www.nuget.org/packages/Microsoft.NETCore.Platforms/) package.</span></span> <span data-ttu-id="89052-132">Listę obsługiwanych identyfikatorów RID i wykres RID można wyświetlić w pliku [*runtime.json,*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) który znajduje się w `dotnet/runtime` repozytorium.</span><span class="sxs-lookup"><span data-stu-id="89052-132">You can see the list of supported RIDs and the RID graph in the [*runtime.json*](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file, which is located at the `dotnet/runtime` repository.</span></span> <span data-ttu-id="89052-133">W tym pliku widać, że wszystkie identyfikatory RID, z `"#import"` wyjątkiem podstawowego, zawierają instrukcję.</span><span class="sxs-lookup"><span data-stu-id="89052-133">In this file, you can see that all RIDs, except for the base one, contain an `"#import"` statement.</span></span> <span data-ttu-id="89052-134">Instrukcje te wskazują zgodne identyfikatory IDENTYFIKATORY.</span><span class="sxs-lookup"><span data-stu-id="89052-134">These statements indicate compatible RIDs.</span></span>

<span data-ttu-id="89052-135">Gdy NuGet przywraca pakiety, próbuje znaleźć dokładne dopasowanie dla określonego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="89052-135">When NuGet restores packages, it tries to find an exact match for the specified runtime.</span></span>
<span data-ttu-id="89052-136">Jeśli dokładne dopasowanie nie zostanie znaleziony, NuGet cofa wykres, dopóki nie znajdzie najbliższego kompatybilnego systemu zgodnie z wykresem RID.</span><span class="sxs-lookup"><span data-stu-id="89052-136">If an exact match is not found, NuGet walks back the graph until it finds the closest compatible system according to the RID graph.</span></span>

<span data-ttu-id="89052-137">Poniższy przykład jest rzeczywisty wpis `osx.10.12-x64` dla RID:</span><span class="sxs-lookup"><span data-stu-id="89052-137">The following example is the actual entry for the `osx.10.12-x64` RID:</span></span>

```json
"osx.10.12-x64": {
    "#import": [ "osx.10.12", "osx.10.11-x64" ]
}
```

<span data-ttu-id="89052-138">Powyższy identyfikator RID `osx.10.12-x64` określa, że importuje `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="89052-138">The above RID specifies that `osx.10.12-x64` imports `osx.10.11-x64`.</span></span> <span data-ttu-id="89052-139">Tak więc, gdy NuGet przywraca pakiety, próbuje `osx.10.12-x64` znaleźć dokładne dopasowanie w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="89052-139">So, when NuGet restores packages, it tries to find an exact match for  `osx.10.12-x64` in the package.</span></span> <span data-ttu-id="89052-140">Jeśli NuGet nie może znaleźć określonego czasu wykonywania, można przywrócić pakiety, które określają `osx.10.11-x64` czas wykonywania, na przykład.</span><span class="sxs-lookup"><span data-stu-id="89052-140">If NuGet cannot find the specific runtime, it can restore packages that specify `osx.10.11-x64` runtimes, for example.</span></span>

<span data-ttu-id="89052-141">W poniższym przykładzie przedstawiono nieco większy wykres RID zdefiniowany również w pliku *runtime.json:*</span><span class="sxs-lookup"><span data-stu-id="89052-141">The following example shows a slightly bigger RID graph also defined in the *runtime.json*  file:</span></span>

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

<span data-ttu-id="89052-142">Wszystkie identyfikatory RID ostatecznie mapują z powrotem do głównego rid. `any`</span><span class="sxs-lookup"><span data-stu-id="89052-142">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="89052-143">Podczas pracy z nimi należy pamiętać o identyfikatorach RID:</span><span class="sxs-lookup"><span data-stu-id="89052-143">There are some considerations about RIDs that you have to keep in mind when working with them:</span></span>

- <span data-ttu-id="89052-144">IDENTYFIKATORY SĄ **nieprzezroczyste ciągi** i powinny być traktowane jako czarne pola.</span><span class="sxs-lookup"><span data-stu-id="89052-144">RIDs are **opaque strings** and should be treated as black boxes.</span></span>
- <span data-ttu-id="89052-145">Nie twórz identyfikatorów RID programowo.</span><span class="sxs-lookup"><span data-stu-id="89052-145">Don't build RIDs programmatically.</span></span>
- <span data-ttu-id="89052-146">Użyj identyfikatorów IDENTYFIKATORÓW, które są już zdefiniowane dla platformy.</span><span class="sxs-lookup"><span data-stu-id="89052-146">Use RIDs that are already defined for the platform.</span></span>
- <span data-ttu-id="89052-147">IDENTYFIKATORY RID muszą być specyficzne, więc nie zakładaj niczego z rzeczywistej wartości RID.</span><span class="sxs-lookup"><span data-stu-id="89052-147">The RIDs need to be specific, so don't assume anything from the actual RID value.</span></span>

## <a name="using-rids"></a><span data-ttu-id="89052-148">Korzystanie z identyfikatorów NIK</span><span class="sxs-lookup"><span data-stu-id="89052-148">Using RIDs</span></span>

<span data-ttu-id="89052-149">Aby móc używać identyfikatorów IDENTYFIKATORÓW, musisz wiedzieć, które identyfikatory IDENTYFIKATORÓw ISTNIEJĄ.</span><span class="sxs-lookup"><span data-stu-id="89052-149">To be able to use RIDs, you have to know which RIDs exist.</span></span> <span data-ttu-id="89052-150">Nowe wartości są regularnie dodawane do platformy.</span><span class="sxs-lookup"><span data-stu-id="89052-150">New values are added regularly to the platform.</span></span>
<span data-ttu-id="89052-151">Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="89052-151">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

<span data-ttu-id="89052-152">.NET Core 2.0 SDK wprowadza koncepcję przenośnych identyfikatorów NIK.</span><span class="sxs-lookup"><span data-stu-id="89052-152">.NET Core 2.0 SDK introduces the concept of portable RIDs.</span></span> <span data-ttu-id="89052-153">Są to nowe wartości dodane do wykresu RID, które nie są powiązane z określoną wersją lub dystrybucją systemu operacyjnego i są preferowanym wyborem podczas korzystania z .NET Core 2.0 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="89052-153">They are new values added to the RID graph that aren't tied to a specific version or OS distribution and are the preferred choice when using .NET Core 2.0 and higher.</span></span> <span data-ttu-id="89052-154">Są one szczególnie przydatne w przypadku wielu dystrybucji Linuksa, ponieważ większość dystrybucji identyfikatorów RID są mapowane na przenośne identyfikatory RID.</span><span class="sxs-lookup"><span data-stu-id="89052-154">They're particularly useful when dealing with multiple Linux distros since most distribution RIDs are mapped to the portable RIDs.</span></span>

<span data-ttu-id="89052-155">Na poniższej liście przedstawiono mały podzbiór najczęściej używanych identyfikatorów NIK używanych dla każdego os.</span><span class="sxs-lookup"><span data-stu-id="89052-155">The following list shows a small subset of the most common RIDs used for each OS.</span></span>

## <a name="windows-rids"></a><span data-ttu-id="89052-156">Identyfikatory RID systemu Windows</span><span class="sxs-lookup"><span data-stu-id="89052-156">Windows RIDs</span></span>

<span data-ttu-id="89052-157">Wyświetlane są tylko typowe wartości.</span><span class="sxs-lookup"><span data-stu-id="89052-157">Only common values are listed.</span></span> <span data-ttu-id="89052-158">Aby uzyskać najnowszą i pełną wersję, zobacz `dotnet/runtime` plik [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="89052-158">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="89052-159">Wersja przenośna (.NET Core 2.0 lub nowsza wersja)</span><span class="sxs-lookup"><span data-stu-id="89052-159">Portable (.NET Core 2.0 or later versions)</span></span>
  - `win-x64`
  - `win-x86`
  - `win-arm`
  - `win-arm64`
- <span data-ttu-id="89052-160">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="89052-160">Windows 7 / Windows Server 2008 R2</span></span>
  - `win7-x64`
  - `win7-x86`
- <span data-ttu-id="89052-161">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="89052-161">Windows 8.1 / Windows Server 2012 R2</span></span>
  - `win81-x64`
  - `win81-x86`
  - `win81-arm`
- <span data-ttu-id="89052-162">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="89052-162">Windows 10 / Windows Server 2016</span></span>
  - `win10-x64`
  - `win10-x86`
  - `win10-arm`
  - `win10-arm64`

<span data-ttu-id="89052-163">Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="89052-163">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows).</span></span>

## <a name="linux-rids"></a><span data-ttu-id="89052-164">Identyfikatory RID linuksa</span><span class="sxs-lookup"><span data-stu-id="89052-164">Linux RIDs</span></span>

<span data-ttu-id="89052-165">Wyświetlane są tylko typowe wartości.</span><span class="sxs-lookup"><span data-stu-id="89052-165">Only common values are listed.</span></span> <span data-ttu-id="89052-166">Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="89052-166">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span> <span data-ttu-id="89052-167">Urządzenia z dystrybucją niewymienioną poniżej mogą współpracować z jedną z przenośnych identyfikatorów NIK.</span><span class="sxs-lookup"><span data-stu-id="89052-167">Devices running a distribution not listed below may work with one of the Portable RIDs.</span></span> <span data-ttu-id="89052-168">Na przykład urządzenia Raspberry Pi z niewymienioną `linux-arm`dystrybucją Linuksa mogą być kierowane do .</span><span class="sxs-lookup"><span data-stu-id="89052-168">For example, Raspberry Pi devices running a Linux distribution not listed can be targeted with `linux-arm`.</span></span>

- <span data-ttu-id="89052-169">Wersja przenośna (.NET Core 2.0 lub nowsza wersja)</span><span class="sxs-lookup"><span data-stu-id="89052-169">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="89052-170">`linux-x64`(Większość dystrybucji pulpitu, takich jak CentOS, Debian, Fedora, Ubuntu i pochodne)</span><span class="sxs-lookup"><span data-stu-id="89052-170">`linux-x64` (Most desktop distributions like CentOS, Debian, Fedora, Ubuntu, and derivatives)</span></span>
  - <span data-ttu-id="89052-171">`linux-musl-x64`(Lekkie dystrybucje za pomocą [musl](https://wiki.musl-libc.org/projects-using-musl.html) jak Alpine Linux)</span><span class="sxs-lookup"><span data-stu-id="89052-171">`linux-musl-x64` (Lightweight distributions using [musl](https://wiki.musl-libc.org/projects-using-musl.html) like Alpine Linux)</span></span>
  - <span data-ttu-id="89052-172">`linux-arm`(Dystrybucje Linuksa działające na ARM jak Raspberry Pi)</span><span class="sxs-lookup"><span data-stu-id="89052-172">`linux-arm` (Linux distributions running on ARM like Raspberry Pi)</span></span>
- <span data-ttu-id="89052-173">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="89052-173">Red Hat Enterprise Linux</span></span>
  - <span data-ttu-id="89052-174">`rhel-x64`(Zastąpiony przez `linux-x64` rhel powyżej wersji 6)</span><span class="sxs-lookup"><span data-stu-id="89052-174">`rhel-x64` (Superseded by `linux-x64` for RHEL above version 6)</span></span>
  - <span data-ttu-id="89052-175">`rhel.6-x64`(.NET Core 2.0 lub nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="89052-175">`rhel.6-x64` (.NET Core 2.0 or later versions)</span></span>
- <span data-ttu-id="89052-176">Tizen (.NET Core 2.0 lub nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="89052-176">Tizen (.NET Core 2.0 or later versions)</span></span>
  - `tizen`
  - `tizen.4.0.0`
  - `tizen.5.0.0`

<span data-ttu-id="89052-177">Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="89052-177">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux).</span></span>

## <a name="macos-rids"></a><span data-ttu-id="89052-178">Identyfikatory RID systemu macOS</span><span class="sxs-lookup"><span data-stu-id="89052-178">macOS RIDs</span></span>

<span data-ttu-id="89052-179">RIDy systemu macOS używają starszej marki "OSX".</span><span class="sxs-lookup"><span data-stu-id="89052-179">macOS RIDs use the older "OSX" branding.</span></span> <span data-ttu-id="89052-180">Wyświetlane są tylko typowe wartości.</span><span class="sxs-lookup"><span data-stu-id="89052-180">Only common values are listed.</span></span> <span data-ttu-id="89052-181">Aby uzyskać najnowszą i pełną wersję, zobacz plik `dotnet/runtime` [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="89052-181">For the latest and complete version, see the [runtime.json](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/runtime.json) file on the `dotnet/runtime` repository.</span></span>

- <span data-ttu-id="89052-182">Wersja przenośna (.NET Core 2.0 lub nowsza wersja)</span><span class="sxs-lookup"><span data-stu-id="89052-182">Portable (.NET Core 2.0 or later versions)</span></span>
  - <span data-ttu-id="89052-183">`osx-x64`(Minimalna wersja systemu operacyjnego to macOS 10.12 Sierra)</span><span class="sxs-lookup"><span data-stu-id="89052-183">`osx-x64` (Minimum OS version is macOS 10.12 Sierra)</span></span>
- <span data-ttu-id="89052-184">macOS 10.10 Yosemite</span><span class="sxs-lookup"><span data-stu-id="89052-184">macOS 10.10  Yosemite</span></span>
  - `osx.10.10-x64`
- <span data-ttu-id="89052-185">macOS 10.11 El Capitan</span><span class="sxs-lookup"><span data-stu-id="89052-185">macOS 10.11 El Capitan</span></span>
  - `osx.10.11-x64`
- <span data-ttu-id="89052-186">macOS 10.12 Sierra (.NET Core 1.1 lub nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="89052-186">macOS 10.12 Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.12-x64`
- <span data-ttu-id="89052-187">macOS 10.13 High Sierra (.NET Core 1.1 lub nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="89052-187">macOS 10.13 High Sierra (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.13-x64`
- <span data-ttu-id="89052-188">macOS 10.14 Mojave (.NET Core 1.1 lub nowsze wersje)</span><span class="sxs-lookup"><span data-stu-id="89052-188">macOS 10.14 Mojave (.NET Core 1.1 or later versions)</span></span>
  - `osx.10.14-x64`

<span data-ttu-id="89052-189">Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="89052-189">For more information, see [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos).</span></span>

## <a name="see-also"></a><span data-ttu-id="89052-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89052-190">See also</span></span>

- [<span data-ttu-id="89052-191">Identyfikatory czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="89052-191">Runtime IDs</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/pkg/Microsoft.NETCore.Platforms/readme.md)
