---
title: Tworzenie pakietów dystrybucji platformy .NET Core
description: Dowiedz się, jak spakować, nazwać i wersja .NET Core do dystrybucji.
author: tmds
ms.date: 10/09/2019
ms.custom: seodec18
ms.openlocfilehash: 715eb944c3e7626696f64e63b874e2f77595cf46
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393583"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="2bc66-103">Tworzenie pakietów dystrybucji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2bc66-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="2bc66-104">Ponieważ platforma .NET Core jest dostępna na więcej i większej liczbie platform, warto dowiedzieć się, jak spakować, nazwać i wersja.</span><span class="sxs-lookup"><span data-stu-id="2bc66-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="2bc66-105">W ten sposób programy obsługi pakietów mogą pomóc w zapewnieniu spójnego środowiska bez względu na to, gdzie użytkownicy zdecydują się na uruchomienie platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2bc66-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="2bc66-106">Ten artykuł jest przydatny dla użytkowników, którzy są:</span><span class="sxs-lookup"><span data-stu-id="2bc66-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="2bc66-107">Podjęto próbę skompilowania platformy .NET Core ze źródła.</span><span class="sxs-lookup"><span data-stu-id="2bc66-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="2bc66-108">Chce wprowadzić zmiany w interfejs wiersza polecenia platformy .NET Core, które mogą mieć wpływ na wynikowy układ lub pakiety.</span><span class="sxs-lookup"><span data-stu-id="2bc66-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="2bc66-109">Układ dysku</span><span class="sxs-lookup"><span data-stu-id="2bc66-109">Disk layout</span></span>

<span data-ttu-id="2bc66-110">Po zainstalowaniu programu .NET Core składa się z kilku składników, które zostały wdrożone w systemie plików:</span><span class="sxs-lookup"><span data-stu-id="2bc66-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
{dotnet_root}                                     (*)
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host                                          (*)
│   └── fxr                                       (*)
│       └── <fxr version>        (2)
├── sdk                                           (*)
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)              (*)
├── packs                                         (*)
│   ├── Microsoft.AspNetCore.App.Ref              (*)
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref                 (*)
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>          (*)
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref          (*)
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref                   (*)
│       └── <netstandard version>        (15)
├── shared                                        (*)
│   ├── Microsoft.NETCore.App                     (*)
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App                  (*)
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All                  (*)
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App              (*)
│       └── <desktop app version> (7)
└── templates                                     (*)
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="2bc66-111">(1) **dotnet** Host (znany również jako "muxer") ma dwie odrębne role: Aktywuj środowisko uruchomieniowe, aby uruchomić aplikację, i aktywuj zestaw SDK, aby wysłać do niego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2bc66-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="2bc66-112">Host to natywny plik wykonywalny (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="2bc66-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="2bc66-113">W przypadku jednego hosta większość innych składników znajduje się w katalogach z wersjami (2, 3, 5, 6).</span><span class="sxs-lookup"><span data-stu-id="2bc66-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="2bc66-114">Oznacza to, że w systemie może być dostępnych wiele wersji, ponieważ są one instalowane obok siebie.</span><span class="sxs-lookup"><span data-stu-id="2bc66-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="2bc66-115">(2) **host/FXR/\<> wersja FXR** zawiera logikę rozpoznawania architektury używaną przez hosta.</span><span class="sxs-lookup"><span data-stu-id="2bc66-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="2bc66-116">Host używa najnowszej hostfxr, która jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="2bc66-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="2bc66-117">Hostfxr jest odpowiedzialny za wybór odpowiedniego środowiska uruchomieniowego podczas wykonywania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="2bc66-118">Na przykład aplikacja skompilowana dla programu .NET Core 2.0.0 używa środowiska uruchomieniowego 2.0.5, gdy jest ono dostępne.</span><span class="sxs-lookup"><span data-stu-id="2bc66-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="2bc66-119">Podobnie hostfxr wybiera odpowiedni zestaw SDK podczas opracowywania.</span><span class="sxs-lookup"><span data-stu-id="2bc66-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="2bc66-120">(3) **wersja zestawu SDK/\<sdk >** zestaw SDK (znany również jako "Narzędzie") to zestaw narzędzi zarządzanych, które są używane do pisania i kompilowania bibliotek i aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="2bc66-121">Zestaw SDK zawiera interfejs wiersza polecenia (CLI) platformy .NET Core, kompilator języków zarządzanych, program MSBuild oraz skojarzone zadania kompilacji i cele, narzędzia NuGet, nowe szablony projektów itd.</span><span class="sxs-lookup"><span data-stu-id="2bc66-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="2bc66-122">(4) **zestaw SDK/NuGetFallbackFolder** zawiera pamięć podręczną pakietów NuGet używanych przez zestaw SDK podczas operacji przywracania, na przykład w przypadku uruchamiania `dotnet restore` lub `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build`.</span></span> <span data-ttu-id="2bc66-123">Ten folder jest używany tylko przed platformą .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="2bc66-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="2bc66-124">Nie można go skompilować ze źródła, ponieważ zawiera wstępnie skompilowane zasoby binarne z `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="2bc66-125">Folder **udostępniony** zawiera struktury.</span><span class="sxs-lookup"><span data-stu-id="2bc66-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="2bc66-126">Struktura udostępniona udostępnia zestaw bibliotek w centralnej lokalizacji, dzięki czemu mogą one być używane przez różne aplikacje.</span><span class="sxs-lookup"><span data-stu-id="2bc66-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="2bc66-127">(5) **współdzielona/Microsoft. rdzeń. app/\<wersja środowiska uruchomieniowego >** to środowisko zawiera środowisko uruchomieniowe platformy .NET Core i obsługujące biblioteki zarządzane.</span><span class="sxs-lookup"><span data-stu-id="2bc66-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="2bc66-128">(6) **Shared/Microsoft. AspNetCore. { Aplikacja, wszystkie}/\<wersja aspnetcore >** zawiera biblioteki ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="2bc66-129">Biblioteki w obszarze `Microsoft.AspNetCore.App` są opracowywane i obsługiwane w ramach projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="2bc66-130">Biblioteki w obszarze `Microsoft.AspNetCore.All` stanowią nadzbiór, który zawiera również biblioteki innych firm.</span><span class="sxs-lookup"><span data-stu-id="2bc66-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="2bc66-131">(7) **udostępniona/Microsoft. Desktop. app/\<wersja aplikacji klasycznej >** zawiera biblioteki pulpitu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bc66-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="2bc66-132">Nie jest to uwzględnione na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="2bc66-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="2bc66-133">(8) **License. txt, ThirdPartyNotices. txt** to licencja platformy .NET Core i licencje bibliotek innych firm używane odpowiednio w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="2bc66-134">(9, 10) **dotnet. 1. gz, dotnet** `dotnet.1.gz` jest stroną ręczną dotnet.</span><span class="sxs-lookup"><span data-stu-id="2bc66-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="2bc66-135">`dotnet` jest link symboliczny hosta dotnet (1).</span><span class="sxs-lookup"><span data-stu-id="2bc66-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="2bc66-136">Te pliki są instalowane w dobrze znanych lokalizacjach na potrzeby integracji systemu.</span><span class="sxs-lookup"><span data-stu-id="2bc66-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="2bc66-137">(11, 12) **Microsoft. servicecore. app. ref, Microsoft. AspNetCore. app. ref** opisują odpowiednio interfejs API `x.y` wersji .NET Core i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="2bc66-138">Te pakiety są używane podczas kompilowania dla tych wersji docelowych.</span><span class="sxs-lookup"><span data-stu-id="2bc66-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="2bc66-139">(13) **Microsoft. WebCore. app. host.\<rid >** zawiera natywny plik binarny dla platformy `rid`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="2bc66-140">Ten plik binarny jest szablonem podczas kompilowania aplikacji .NET Core do natywnego pliku binarnego dla tej platformy.</span><span class="sxs-lookup"><span data-stu-id="2bc66-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="2bc66-141">(14) **Microsoft. WindowsDesktop. app. ref** — zawiera opis interfejsu API `x.y` wersji aplikacji klasycznych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bc66-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="2bc66-142">Te pliki są używane podczas kompilowania dla tego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2bc66-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="2bc66-143">Nie jest to obsługiwane na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="2bc66-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="2bc66-144">(15) **Standard. Library. ref** — opisuje standardowy interfejs API `x.y`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="2bc66-145">Te pliki są używane podczas kompilowania dla tego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2bc66-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="2bc66-146">(16) **/etc/dotnet/install_location** jest plikiem, który zawiera pełną ścieżkę `{dotnet_root}`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-146">(16) **/etc/dotnet/install_location** is a file that contains the full path for `{dotnet_root}`.</span></span> <span data-ttu-id="2bc66-147">Ścieżka może kończyć się znakiem nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="2bc66-147">The path may end with a newline.</span></span> <span data-ttu-id="2bc66-148">Nie trzeba dodawać tego pliku, gdy katalog główny jest `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="2bc66-149">**Szablony** (17) zawierają szablony używane przez zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="2bc66-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="2bc66-150">Na przykład `dotnet new` odnajdzie szablony projektu tutaj.</span><span class="sxs-lookup"><span data-stu-id="2bc66-150">For example, `dotnet new` finds project templates here.</span></span>

<span data-ttu-id="2bc66-151">Foldery oznaczone `(*)` są używane przez wiele pakietów.</span><span class="sxs-lookup"><span data-stu-id="2bc66-151">The folders marked with `(*)` are used by multiple packages.</span></span> <span data-ttu-id="2bc66-152">Niektóre formaty pakietów (na przykład `rpm`) wymagają specjalnej obsługi takich folderów.</span><span class="sxs-lookup"><span data-stu-id="2bc66-152">Some package formats (for example, `rpm`) require special handling of such folders.</span></span> <span data-ttu-id="2bc66-153">Należy zachować ostrożność nad pakietem.</span><span class="sxs-lookup"><span data-stu-id="2bc66-153">The package maintainer must take care of this.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="2bc66-154">Zalecane pakiety</span><span class="sxs-lookup"><span data-stu-id="2bc66-154">Recommended packages</span></span>

<span data-ttu-id="2bc66-155">Wersja .NET Core jest oparta na składniku środowiska uruchomieniowego `[major].[minor]` numerach wersji.</span><span class="sxs-lookup"><span data-stu-id="2bc66-155">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="2bc66-156">Wersja zestawu SDK używa tego samego `[major].[minor]` i ma niezależną `[patch]`, która łączy semantykę funkcji i poprawek dla zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="2bc66-156">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="2bc66-157">Na przykład: zestaw SDK w wersji 2.2.302 to druga wersja poprawki zestawu SDK, która obsługuje środowisko uruchomieniowe 2,2.</span><span class="sxs-lookup"><span data-stu-id="2bc66-157">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="2bc66-158">Aby uzyskać więcej informacji o działaniu wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bc66-158">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="2bc66-159">Niektóre pakiety zawierają część numeru wersji w nazwie.</span><span class="sxs-lookup"><span data-stu-id="2bc66-159">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="2bc66-160">Pozwala to na zainstalowanie określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="2bc66-160">This allows you to install a specific version.</span></span>
<span data-ttu-id="2bc66-161">Reszta wersji nie jest uwzględniona w nazwie wersji.</span><span class="sxs-lookup"><span data-stu-id="2bc66-161">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="2bc66-162">Dzięki temu Menedżer pakietów systemu operacyjnego może aktualizować pakiety (na przykład automatycznie instalując poprawki zabezpieczeń).</span><span class="sxs-lookup"><span data-stu-id="2bc66-162">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="2bc66-163">Obsługiwane menedżery pakietów są specyficzne dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="2bc66-163">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="2bc66-164">Poniżej przedstawiono listę zalecanych pakietów:</span><span class="sxs-lookup"><span data-stu-id="2bc66-164">The following lists the recommended packages:</span></span>

- <span data-ttu-id="2bc66-165">`dotnet-sdk-[major].[minor]` — instaluje najnowszy zestaw SDK dla określonego środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2bc66-165">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="2bc66-166">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-166">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-167">**Przykład:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="2bc66-167">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="2bc66-168">**Zawiera:** (3), (4)</span><span class="sxs-lookup"><span data-stu-id="2bc66-168">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="2bc66-169">**Zależności:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2bc66-169">**Dependencies:** `dotnet-runtime-[major].[minor]`, `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="2bc66-170">`aspnetcore-runtime-[major].[minor]` — instaluje określony ASP.NET Core środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2bc66-170">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="2bc66-171">**Wersja:** \<wersja środowiska uruchomieniowego aspnetcore ></span><span class="sxs-lookup"><span data-stu-id="2bc66-171">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2bc66-172">**Przykład:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2bc66-172">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="2bc66-173">**Zawiera:** (6)</span><span class="sxs-lookup"><span data-stu-id="2bc66-173">**Contains:** (6)</span></span>
  - <span data-ttu-id="2bc66-174">**Zależności:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2bc66-174">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="2bc66-175">`dotnet-runtime-deps-[major].[minor]` _(opcjonalnie)_ — instaluje zależności do uruchamiania aplikacji samodzielnych</span><span class="sxs-lookup"><span data-stu-id="2bc66-175">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="2bc66-176">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-176">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-177">**Przykład:** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="2bc66-177">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="2bc66-178">**Zależności:** _dystrybucji określonych zależności_</span><span class="sxs-lookup"><span data-stu-id="2bc66-178">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="2bc66-179">`dotnet-runtime-[major].[minor]` — instaluje określone środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2bc66-179">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="2bc66-180">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-180">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-181">**Przykład:** dotnet-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="2bc66-181">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="2bc66-182">**Zawiera:** (5)</span><span class="sxs-lookup"><span data-stu-id="2bc66-182">**Contains:** (5)</span></span>
  - <span data-ttu-id="2bc66-183">**Zależności:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="2bc66-183">**Dependencies:** `dotnet-hostfxr-[major].[minor]`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="2bc66-184">`dotnet-hostfxr-[major].[minor]` — zależność</span><span class="sxs-lookup"><span data-stu-id="2bc66-184">`dotnet-hostfxr-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2bc66-185">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-185">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-186">**Przykład:** dotnet-hostfxr-3,0</span><span class="sxs-lookup"><span data-stu-id="2bc66-186">**Example:** dotnet-hostfxr-3.0</span></span>
  - <span data-ttu-id="2bc66-187">**Zawiera:** (2)</span><span class="sxs-lookup"><span data-stu-id="2bc66-187">**Contains:** (2)</span></span>
  - <span data-ttu-id="2bc66-188">**Zależności:** `dotnet-host`</span><span class="sxs-lookup"><span data-stu-id="2bc66-188">**Dependencies:** `dotnet-host`</span></span>

- <span data-ttu-id="2bc66-189">`dotnet-host` — zależność</span><span class="sxs-lookup"><span data-stu-id="2bc66-189">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="2bc66-190">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-190">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-191">**Przykład:** dotnet-Host</span><span class="sxs-lookup"><span data-stu-id="2bc66-191">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="2bc66-192">**Zawiera:** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="2bc66-192">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="2bc66-193">`dotnet-apphost-pack-[major].[minor]` — zależność</span><span class="sxs-lookup"><span data-stu-id="2bc66-193">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="2bc66-194">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-195">**Zawiera:** (13)</span><span class="sxs-lookup"><span data-stu-id="2bc66-195">**Contains:** (13)</span></span>

- <span data-ttu-id="2bc66-196">`dotnet-targeting-pack-[major].[minor]` — umożliwia kierowanie do nienajnowszego środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2bc66-196">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2bc66-197">**Wersja:** \<wersja środowiska uruchomieniowego ></span><span class="sxs-lookup"><span data-stu-id="2bc66-197">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="2bc66-198">**Zawiera:** (12)</span><span class="sxs-lookup"><span data-stu-id="2bc66-198">**Contains:** (12)</span></span>

- <span data-ttu-id="2bc66-199">`aspnetcore-targeting-pack-[major].[minor]` — umożliwia kierowanie do nienajnowszego środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="2bc66-199">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="2bc66-200">**Wersja:** \<wersja środowiska uruchomieniowego aspnetcore ></span><span class="sxs-lookup"><span data-stu-id="2bc66-200">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="2bc66-201">**Zawiera:** (11)</span><span class="sxs-lookup"><span data-stu-id="2bc66-201">**Contains:** (11)</span></span>

- <span data-ttu-id="2bc66-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` — umożliwia kierowanie do wersji standardowej</span><span class="sxs-lookup"><span data-stu-id="2bc66-202">`netstandard-targeting-pack-[netstandard_major].[netstandard_minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="2bc66-203">**Wersja:** wersja zestawu sdk \<></span><span class="sxs-lookup"><span data-stu-id="2bc66-203">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2bc66-204">**Zawiera:** (15)</span><span class="sxs-lookup"><span data-stu-id="2bc66-204">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="2bc66-205">**Wersja:** wersja zestawu sdk \<></span><span class="sxs-lookup"><span data-stu-id="2bc66-205">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="2bc66-206">**Zawiera:** (15)</span><span class="sxs-lookup"><span data-stu-id="2bc66-206">**Contains:** (15)</span></span>

<span data-ttu-id="2bc66-207">`dotnet-runtime-deps-[major].[minor]` wymaga interpretacji _zależności specyficznych dla dystrybucji_.</span><span class="sxs-lookup"><span data-stu-id="2bc66-207">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro-specific dependencies_.</span></span> <span data-ttu-id="2bc66-208">Ponieważ system kompilacji dystrybucji może być w stanie automatycznie dziedziczyć, pakiet jest opcjonalny, w takim przypadku te zależności są dodawane bezpośrednio do pakietu `dotnet-runtime-[major].[minor]`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-208">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="2bc66-209">Gdy zawartość pakietu znajduje się w folderze z uruchomioną wersją, nazwa pakietu `[major].[minor]` być zgodna z nazwą folderu z wersją.</span><span class="sxs-lookup"><span data-stu-id="2bc66-209">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="2bc66-210">Wszystkie pakiety, z wyjątkiem `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, są również zgodne z wersją .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bc66-210">For all packages, except the `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="2bc66-211">Zależności między pakietami powinny mieć wartość _równą lub większą niż_ wymaganie wersji.</span><span class="sxs-lookup"><span data-stu-id="2bc66-211">Dependencies between packages should use an _equal or greater than_ version requirement.</span></span> <span data-ttu-id="2bc66-212">Na przykład `dotnet-sdk-2.2:2.2.401` wymaga `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-212">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="2bc66-213">Dzięki temu użytkownik może uaktualnić instalację za pośrednictwem pakietu głównego (na przykład `dnf update dotnet-sdk-2.2`).</span><span class="sxs-lookup"><span data-stu-id="2bc66-213">This makes it possible for the user to upgrade their installation via a root package (for example, `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="2bc66-214">Większość dystrybucji wymaga, aby wszystkie artefakty zostały skompilowane ze źródła.</span><span class="sxs-lookup"><span data-stu-id="2bc66-214">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="2bc66-215">Ma to wpływ na pakiety:</span><span class="sxs-lookup"><span data-stu-id="2bc66-215">This has some impact on the packages:</span></span>

- <span data-ttu-id="2bc66-216">Bibliotek innych firm w `shared/Microsoft.AspNetCore.All` nie można z łatwością skompilować ze źródła.</span><span class="sxs-lookup"><span data-stu-id="2bc66-216">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="2bc66-217">Ten folder zostanie pominięty w pakiecie `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-217">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="2bc66-218">`NuGetFallbackFolder` jest wypełniana przy użyciu artefaktów binarnych z `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-218">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="2bc66-219">Powinna pozostać pusta.</span><span class="sxs-lookup"><span data-stu-id="2bc66-219">It should remain empty.</span></span>

<span data-ttu-id="2bc66-220">Wiele pakietów `dotnet-sdk` może zapewnić te same pliki dla `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="2bc66-220">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="2bc66-221">Aby uniknąć problemów z menedżerem pakietów, te pliki powinny być identyczne (suma kontrolna, Data modyfikacji itd.).</span><span class="sxs-lookup"><span data-stu-id="2bc66-221">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="2bc66-222">Kompilowanie pakietów</span><span class="sxs-lookup"><span data-stu-id="2bc66-222">Building packages</span></span>

<span data-ttu-id="2bc66-223">Repozytorium [dotnet/Source-Build](https://github.com/dotnet/source-build) zawiera instrukcje dotyczące sposobu tworzenia źródłowej plik tar zestaw .NET Core SDK i wszystkich jego składników.</span><span class="sxs-lookup"><span data-stu-id="2bc66-223">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="2bc66-224">Dane wyjściowe repozytorium Build source są zgodne z układem opisanym w pierwszej sekcji tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="2bc66-224">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
