---
title: Usuwanie czasu uruchomieniowego i sdk programu .NET Core
description: W tym artykule opisano sposób określania, które wersje środowiska uruchomieniowego i sdk .NET Core są aktualnie zainstalowane, a następnie jak je usunąć w systemach Windows, Mac i Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398840"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="f9d3b-103">Jak usunąć program .NET Core Runtime i SDK</span><span class="sxs-lookup"><span data-stu-id="f9d3b-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="f9d3b-104">Wraz z urazem, po zainstalowaniu zaktualizowanych wersji programu .NET Core i sdk, można usunąć nieaktualne wersje programu .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="f9d3b-105">Usunięcie starszych wersji programu runtime może zmienić czas wykonywania wybrany do uruchamiania udostępnionych aplikacji framework, jak wyszczególniono w artykule na [.NET Core wybór wersji](selection.md).</span><span class="sxs-lookup"><span data-stu-id="f9d3b-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="f9d3b-106">Czy należy usunąć wersję?</span><span class="sxs-lookup"><span data-stu-id="f9d3b-106">Should I remove a version?</span></span>

<span data-ttu-id="f9d3b-107">Zachowania [wyboru wersji .NET Core](selection.md) i zgodność programu .NET Core w aktualizacjach umożliwiają bezpieczne usuwanie poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="f9d3b-108">Aktualizacje środowiska uruchomieniowego .NET Core są zgodne w ramach głównej wersji "pasma", takiej jak 1.x i 2.x.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="f9d3b-109">Ponadto nowsze wersje .NET Core SDK zazwyczaj zachowują możliwość tworzenia aplikacji, które są przeznaczone dla poprzednich wersji środowiska uruchomieniowego w sposób zgodny.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="f9d3b-110">Ogólnie rzecz biorąc, potrzebujesz tylko najnowszego sdk i najnowszej wersji poprawki w czasie wykonywania wymaganych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="f9d3b-111">Wystąpienia, w których przechowywanie starszych wersji sdk lub runtime obejmują utrzymanie aplikacji opartych na **project.json.**</span><span class="sxs-lookup"><span data-stu-id="f9d3b-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="f9d3b-112">Chyba że aplikacja ma konkretne powody wcześniejszych zestawów SDK lub kręgów, można bezpiecznie usunąć starsze wersje.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="f9d3b-113">Określanie, co jest zainstalowane</span><span class="sxs-lookup"><span data-stu-id="f9d3b-113">Determine what is installed</span></span>

<span data-ttu-id="f9d3b-114">Począwszy od .NET Core 2.1, .NET CLI ma opcje, których można użyć do wyświetlenia wersji sdk i czasu uruchomieniowego, które są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="f9d3b-115">Służy [`dotnet --list-sdks`](../tools/dotnet.md#options) do wyświetlanie listy zestawów SDK zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="f9d3b-116">Służy [`dotnet --list-runtimes`](../tools/dotnet.md#options) do wyświetlanie listy uruchomień zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="f9d3b-117">Poniższy tekst przedstawia typowe dane wyjściowe dla systemów Windows, macOS lub Linux:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="f9d3b-118">Windows</span><span class="sxs-lookup"><span data-stu-id="f9d3b-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="f9d3b-119">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="f9d3b-120">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-120">You get output similar to the following:</span></span>

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

<span data-ttu-id="f9d3b-121">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="f9d3b-122">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-122">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[<span data-ttu-id="f9d3b-123">Linux</span><span class="sxs-lookup"><span data-stu-id="f9d3b-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="f9d3b-124">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="f9d3b-125">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-125">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

<span data-ttu-id="f9d3b-126">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="f9d3b-127">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-127">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[<span data-ttu-id="f9d3b-128">Macos</span><span class="sxs-lookup"><span data-stu-id="f9d3b-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="f9d3b-129">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="f9d3b-130">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-130">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

<span data-ttu-id="f9d3b-131">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="f9d3b-132">Otrzymujesz dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-132">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a><span data-ttu-id="f9d3b-133">Odinstaluj program .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9d3b-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="f9d3b-134">Windows</span><span class="sxs-lookup"><span data-stu-id="f9d3b-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="f9d3b-135">Program .NET Core używa okna dialogowego **Dodawanie/usuwanie programów** systemu Windows w celu usunięcia wersji środowiska uruchomieniowego i sdk programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="f9d3b-136">Na poniższej ilustracji przedstawiono okno **dialogowe Dodawanie/usuwanie programów** z kilkoma wersjami zainstalowanego programu .NET i sdk.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Dodawanie / usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="f9d3b-138">Wybierz dowolne wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="f9d3b-139">Linux</span><span class="sxs-lookup"><span data-stu-id="f9d3b-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="f9d3b-140">Istnieje więcej opcji odinstalowania programu .NET Core (sdk lub w czasie wykonywania) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="f9d3b-141">Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="f9d3b-142">Specyfika zależy od wybranej dystrybucji i metody instalacji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f9d3b-143">W przypadku instalacji programu Red Hat zapoznaj się z [przewodnikiem Red Hat Wprowadzenie,](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="f9d3b-144">Począwszy od .NET Core 2.1, nie ma potrzeby odinstalowywania zestawu SDK .NET Core podczas uaktualniania go za pomocą Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="f9d3b-145">Menedżer `update` pakietów `refresh` lub polecenia automatycznie usunie starszą wersję po pomyślnej instalacji nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="f9d3b-146">Jeśli program .NET Core został zainstalowany przy użyciu menedżera pakietów, do odinstalowania zestawu SDK lub programu runtime jest używany przez tego samego menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="f9d3b-147">Instalacje .NET Core obsługują najpopularniejsze menedżery pakietów.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="f9d3b-148">Dokładne opis składni środowiska można znaleźć w dokumentacji menedżera pakietów dystrybucji:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="f9d3b-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy debianowe, w tym Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="f9d3b-150">[yum(8)](https://linux.die.net/man/8/yum) jest używany w Fedorze, CentOS i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="f9d3b-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w openSUSE i SUSE Linux Enterprise System (SLES).</span><span class="sxs-lookup"><span data-stu-id="f9d3b-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="f9d3b-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest stosowany w Fedorze.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="f9d3b-153">W prawie wszystkich przypadkach polecenie usunięcia `remove`pakietu jest .</span><span class="sxs-lookup"><span data-stu-id="f9d3b-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="f9d3b-154">Nazwa pakietu dla instalacji sdk .NET Core `dotnet-sdk`dla większości menedżerów pakietów to , po którym następuje numer wersji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="f9d3b-155">Począwszy od wersji 2.1.300 zestawu .NET Core `2.1` SDK i wersji programu runtime, wymagane są tylko numery wersji głównych i pomocniczych: na przykład jako pakiet `dotnet-sdk-2.1`można odwoływać się do zestawu .NET Core SDK w wersji 2.1.300 .</span><span class="sxs-lookup"><span data-stu-id="f9d3b-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="f9d3b-156">Wcześniejsze wersje wymagają całego ciągu `dotnet-sdk-2.1.200` wersji: na przykład będzie wymagane dla wersji 2.1.200 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="f9d3b-157">W przypadku komputerów, które zainstalowały tylko czas wykonywania, a `dotnet-runtime-<version>` nie zestaw SDK, `aspnetcore-runtime-<version>` nazwa pakietu jest dla programu runtime .NET Core i dla całego stosu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="f9d3b-158">Instalacje programu .NET Core wcześniejsze niż 2.0 nie odinstalowano aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="f9d3b-159">Za `apt-get`pomocą polecenia jest:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="f9d3b-160">Należy pamiętać, że nie `dotnet-host`ma dołączonej wersji .</span><span class="sxs-lookup"><span data-stu-id="f9d3b-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="f9d3b-161">Jeśli zainstalowano przy użyciu tarball, należy usunąć .NET Core przy użyciu metody ręcznej.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="f9d3b-162">Zestawy SDK i programy wykonywania są usuwane oddzielnie, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="f9d3b-163">Na przykład, aby usunąć zestaw SDK 1.0.1 i czas wykonywania, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="f9d3b-164">Katalogi nadrzędne dla sdk i czasu wykonywania są `dotnet --list-sdks` `dotnet --list-runtimes` wyświetlane w danych wyjściowych z i polecenia, jak pokazano we wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="f9d3b-165">Macos</span><span class="sxs-lookup"><span data-stu-id="f9d3b-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="f9d3b-166">Na komputerze Mac należy usunąć zestawy SDK i programy wykonywania oddzielnie, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="f9d3b-167">Na przykład, aby usunąć zestaw SDK 1.0.1 i czas wykonywania, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="f9d3b-168">Katalogi nadrzędne dla sdk i czasu wykonywania są `dotnet --list-sdks` `dotnet --list-runtimes` wyświetlane w danych wyjściowych z i polecenia, jak pokazano we wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="f9d3b-169">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9d3b-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="f9d3b-170">[Narzędzie .NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umożliwia usunięcie zestawów SDK i runi .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="f9d3b-171">Dostępna jest kolekcja opcji określających, które wersje mają zostać odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="f9d3b-172">Zależność programu Visual Studio od wersji sdk programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9d3b-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="f9d3b-173">Przed programiem Visual Studio 2019 w wersji 16.3 instalatory programu Visual Studio nazywali samodzielnyinstalator sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="f9d3b-174">W rezultacie wersje sdk są wyświetlane w oknie dialogowym **Dodawanie/usuwanie programów** systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="f9d3b-175">Usunięcie zestawów SDK .NET Core, które zostały zainstalowane przez program Visual Studio przy użyciu instalatora autonomicznego, może snąć program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="f9d3b-176">Jeśli program Visual Studio ma problemy po odinstalowaniu zestawów SDK, uruchom program Repair w tej określonej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="f9d3b-177">W poniższej tabeli przedstawiono niektóre zależności programu Visual Studio w wersjach sdk programu .NET Core:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="f9d3b-178">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9d3b-178">Visual Studio version</span></span> | <span data-ttu-id="f9d3b-179">Wersja SDK programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9d3b-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="f9d3b-180"> Program Visual Studio 2019 w wersji 16.2 </span><span class="sxs-lookup"><span data-stu-id="f9d3b-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="f9d3b-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span><span class="sxs-lookup"><span data-stu-id="f9d3b-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="f9d3b-182">Visual Studio 2019 w wersji 16.1</span><span class="sxs-lookup"><span data-stu-id="f9d3b-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="f9d3b-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span><span class="sxs-lookup"><span data-stu-id="f9d3b-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="f9d3b-184">Visual Studio 2019 w wersji 16.0</span><span class="sxs-lookup"><span data-stu-id="f9d3b-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="f9d3b-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span><span class="sxs-lookup"><span data-stu-id="f9d3b-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="f9d3b-186">Visual Studio 2017 w wersji 15.9</span><span class="sxs-lookup"><span data-stu-id="f9d3b-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="f9d3b-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span><span class="sxs-lookup"><span data-stu-id="f9d3b-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="f9d3b-188">Program Visual Studio 2017 w wersji 15.8</span><span class="sxs-lookup"><span data-stu-id="f9d3b-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="f9d3b-189">.NET Core SDK 2.1.4xx</span><span class="sxs-lookup"><span data-stu-id="f9d3b-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="f9d3b-190">Począwszy od programu Visual Studio 2019 w wersji 16.3, program Visual Studio jest odpowiedzialny za własną kopię .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="f9d3b-191">Z tego powodu nie są już widoczne te wersje sdk w oknie dialogowym **Dodawanie/usuwanie programów.**</span><span class="sxs-lookup"><span data-stu-id="f9d3b-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="f9d3b-192">Usuwanie folderu rezerwowego NuGet</span><span class="sxs-lookup"><span data-stu-id="f9d3b-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="f9d3b-193">Przed zestawem SDK .NET Core 3.0 instalatorzy sdk .NET Core używali *NuGetFallbackFolder* do przechowywania pamięci podręcznej pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="f9d3b-194">Ta pamięć podręczna `dotnet restore` była `dotnet build /t:Restore`używana podczas operacji, takich jak lub .</span><span class="sxs-lookup"><span data-stu-id="f9d3b-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="f9d3b-195">Znajduje `NuGetFallbackFolder` się w *C:\Program Files\dotnet\sdk* w systemie Windows oraz w */usr/local/share/dotnet/sdk* w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="f9d3b-196">Możesz usunąć ten folder, jeśli:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="f9d3b-197">Tworzysz tylko przy użyciu .NET Core 3.0 SDK lub nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="f9d3b-198">Tworzysz przy użyciu .NET Core SDK wersje wcześniej niż 3.0, ale można pracować w trybie online i rzeczy mogą być wolniejsze raz.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="f9d3b-199">Jeśli chcesz usunąć folder rezerwowy NuGet, możesz go usunąć, ale do tego potrzebne są uprawnienia administratora.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="f9d3b-200">Nie zaleca się usuwania folderu *dotnet.*</span><span class="sxs-lookup"><span data-stu-id="f9d3b-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="f9d3b-201">Spowoduje to usunięcie wszystkich narzędzi globalnych, które zostały wcześniej zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="f9d3b-202">Ponadto w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="f9d3b-202">Also, on Windows:</span></span>

- <span data-ttu-id="f9d3b-203">Złamiesz visual studio 2019 w wersji 16.3 i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="f9d3b-204">Można uruchomić **naprawa,** aby odzyskać.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="f9d3b-205">Jeśli w oknie dialogowym **Dodawanie/usuwanie programów** znajdują się wpisy sdk .NET Core, zostaną one oddzielone.</span><span class="sxs-lookup"><span data-stu-id="f9d3b-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
