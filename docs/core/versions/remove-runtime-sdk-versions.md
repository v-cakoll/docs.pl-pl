---
title: Usuwanie środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule opisano sposób ustalania, które wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core są obecnie zainstalowane, a następnie sposobu ich usuwania w systemach Windows, Mac i Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 6d1012b8ddc5fd4a5ee8227902886727dbb10739
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970296"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="789ac-103">Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="789ac-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="789ac-104">Wraz z upływem czasu podczas instalowania zaktualizowanych wersji środowiska uruchomieniowego .NET Core i zestawu SDK można usunąć nieaktualne wersje programu .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="789ac-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="789ac-105">Usunięcie starszych wersji środowiska uruchomieniowego może zmienić środowisko uruchomieniowe wybrane do uruchamiania aplikacji platformy udostępnionej, zgodnie z opisem w artykule na temat [wyboru wersji platformy .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="789ac-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="789ac-106">Czy należy usunąć wersję?</span><span class="sxs-lookup"><span data-stu-id="789ac-106">Should I remove a version?</span></span>

<span data-ttu-id="789ac-107">Zachowania [wyboru wersji .NET Core](selection.md) i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwiają bezpieczne usuwanie poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="789ac-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="789ac-108">Aktualizacje środowiska uruchomieniowego programu .NET Core są zgodne z wersją główną "Band", taką jak 1. x i 2. x.</span><span class="sxs-lookup"><span data-stu-id="789ac-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="789ac-109">Ponadto nowsze wersje zestaw .NET Core SDK zwykle utrzymują możliwość tworzenia aplikacji przeznaczonych dla wcześniejszych wersji środowiska uruchomieniowego w sposób zgodny.</span><span class="sxs-lookup"><span data-stu-id="789ac-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="789ac-110">Ogólnie rzecz biorąc potrzebny jest tylko najnowszy zestaw SDK i Najnowsza wersja poprawki środowiska uruchomieniowego, które są wymagane dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="789ac-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="789ac-111">Wystąpienia, w których zachowano starsze wersje zestawu SDK lub środowiska uruchomieniowego, obejmują obsługę aplikacji opartych na **programie Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="789ac-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="789ac-112">Jeśli aplikacja nie ma określonych powodów dla wcześniejszych zestawów SDK lub środowisk uruchomieniowych, możesz bezpiecznie usunąć starsze wersje.</span><span class="sxs-lookup"><span data-stu-id="789ac-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="789ac-113">Określ, co jest zainstalowane</span><span class="sxs-lookup"><span data-stu-id="789ac-113">Determine what is installed</span></span>

<span data-ttu-id="789ac-114">Począwszy od platformy .NET Core 2,1, interfejs wiersza polecenia platformy .NET zawiera opcje, których można użyć do wyświetlenia listy wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="789ac-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="789ac-115">Użyj [`dotnet --list-sdks`](../tools/dotnet.md#options) , aby wyświetlić listę zestawów SDK zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="789ac-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="789ac-116">Użyj [`dotnet --list-runtimes`](../tools/dotnet.md#options) , aby wyświetlić listę środowisk uruchomieniowych zainstalowanych na maszynie.</span><span class="sxs-lookup"><span data-stu-id="789ac-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="789ac-117">Poniższy tekst przedstawia typowe dane wyjściowe dla systemu Windows, macOS lub Linux:</span><span class="sxs-lookup"><span data-stu-id="789ac-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[<span data-ttu-id="789ac-118">Windows</span><span class="sxs-lookup"><span data-stu-id="789ac-118">Windows</span></span>](#tab/windows)

```console
C:\> dotnet --list-sdks
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

C:\> dotnet --list-runtimes
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

# <a name="linuxtablinux"></a>[<span data-ttu-id="789ac-119">Linux</span><span class="sxs-lookup"><span data-stu-id="789ac-119">Linux</span></span>](#tab/linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
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

# <a name="macostabmacos"></a>[<span data-ttu-id="789ac-120">macOS</span><span class="sxs-lookup"><span data-stu-id="789ac-120">macOS</span></span>](#tab/macos)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
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

## <a name="uninstalling-net-core"></a><span data-ttu-id="789ac-121">Odinstalowywanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="789ac-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="789ac-122">Windows</span><span class="sxs-lookup"><span data-stu-id="789ac-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="789ac-123">.NET Core używa okna dialogowego **Dodawanie/usuwanie programów** systemu Windows do usuwania wersji środowiska uruchomieniowego i zestawu SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="789ac-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="789ac-124">Na poniższej ilustracji przedstawiono okno dialogowe **Dodawanie/usuwanie programów** z kilkoma wersjami środowiska uruchomieniowego .NET i ZAINSTALOWANYm zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="789ac-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Dodawanie/usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="789ac-126">Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="789ac-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="789ac-127">Linux</span><span class="sxs-lookup"><span data-stu-id="789ac-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="789ac-128">Istnieje więcej opcji odinstalowywania platformy .NET Core (zestawu SDK lub środowiska uruchomieniowego) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="789ac-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="789ac-129">Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="789ac-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="789ac-130">Informacje te zależą od wybranej dystrybucji i metody instalacji.</span><span class="sxs-lookup"><span data-stu-id="789ac-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="789ac-131">Aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core, należy zapoznać się z [przewodnikiem](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) w witrynie red Hat wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="789ac-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="789ac-132">Począwszy od platformy .NET Core 2,1, nie ma potrzeby odinstalowywania zestaw .NET Core SDK podczas uaktualniania go przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="789ac-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="789ac-133">Menedżer `update` pakietów lub `refresh` polecenia automatycznie usuwają starszą wersję po pomyślnej instalacji nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="789ac-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="789ac-134">Jeśli zainstalowano program .NET Core przy użyciu Menedżera pakietów, należy użyć tego samego Menedżera pakietów do odinstalowania zestawu .NET SDK lub środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="789ac-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="789ac-135">Instalacje .NET Core obsługują najpopularniejszych menedżerów pakietów.</span><span class="sxs-lookup"><span data-stu-id="789ac-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="789ac-136">Zapoznaj się z dokumentacją Menedżera pakietów dystrybucji, aby uzyskać dokładną składnię w Twoim środowisku:</span><span class="sxs-lookup"><span data-stu-id="789ac-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="789ac-137">[apt-get (8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy oparte na Debian, w tym Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="789ac-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="789ac-138">[yum (8)](https://linux.die.net/man/8/yum) jest używany na Fedora, CentOS i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="789ac-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="789ac-139">[użyciu narzędzia zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w systemach OPENSUSE i SUSE Linux Enterprise System (SLES).</span><span class="sxs-lookup"><span data-stu-id="789ac-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="789ac-140">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest używany w Fedora.</span><span class="sxs-lookup"><span data-stu-id="789ac-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="789ac-141">Niemal we wszystkich przypadkach polecenie usunięcia pakietu ma `remove`wartość.</span><span class="sxs-lookup"><span data-stu-id="789ac-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="789ac-142">Nazwa pakietu zestaw .NET Core SDK instalacji dla większości menedżerów pakietów ma `dotnet-sdk`numer wersji.</span><span class="sxs-lookup"><span data-stu-id="789ac-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="789ac-143">Począwszy od wersji 2.1.300 zestaw .NET Core SDK i wersji `2.1` środowiska uruchomieniowego, wymagane są tylko główne i pomocnicze numery wersji: na przykład zestaw .NET Core SDK wersja 2.1.300 może być przywoływana jako pakiet. `dotnet-sdk-2.1`</span><span class="sxs-lookup"><span data-stu-id="789ac-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="789ac-144">Wcześniejsze wersje wymagają, aby cały ciąg wersji był wymagany, `dotnet-sdk-2.1.200` na przykład w przypadku wersji 2.1.200 zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="789ac-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="789ac-145">W przypadku maszyn, na których zainstalowano tylko środowisko uruchomieniowe, a nie zestawu SDK `dotnet-runtime-<version>` , nazwa pakietu jest dla środowiska uruchomieniowego .NET Core oraz `aspnetcore-runtime-<version>` dla całego stosu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="789ac-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="789ac-146">Instalacje .NET Core przed 2,0 nie odinstalowały aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="789ac-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="789ac-147">Za `apt-get`pomocą polecenia jest:</span><span class="sxs-lookup"><span data-stu-id="789ac-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="789ac-148">Należy zauważyć, że nie ma żadnej wersji `dotnet-host`dołączonej do programu.</span><span class="sxs-lookup"><span data-stu-id="789ac-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="789ac-149">Jeśli zainstalowano program przy użyciu plik tar, należy usunąć platformę .NET Core przy użyciu metody ręcznej.</span><span class="sxs-lookup"><span data-stu-id="789ac-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="789ac-150">Zestawy SDK i środowiska uruchomieniowe należy usunąć oddzielnie, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="789ac-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="789ac-151">Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="789ac-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="789ac-152">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="789ac-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="789ac-153">macOS</span><span class="sxs-lookup"><span data-stu-id="789ac-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="789ac-154">Na komputerach Mac należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="789ac-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="789ac-155">Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="789ac-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="789ac-156">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych `dotnet --list-sdks` wyjściowych `dotnet --list-runtimes` polecenia i, jak pokazano w wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="789ac-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
