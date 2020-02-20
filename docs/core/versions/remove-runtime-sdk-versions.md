---
title: Usuwanie środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule opisano sposób ustalania, które wersje środowiska uruchomieniowego i zestawu SDK platformy .NET Core są obecnie zainstalowane, a następnie sposobu ich usuwania w systemach Windows, Mac i Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503465"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="01348-103">Jak usunąć środowisko uruchomieniowe programu .NET Core i zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="01348-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="01348-104">Wraz z upływem czasu podczas instalowania zaktualizowanych wersji środowiska uruchomieniowego .NET Core i zestawu SDK można usunąć nieaktualne wersje programu .NET Core z komputera.</span><span class="sxs-lookup"><span data-stu-id="01348-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="01348-105">Usunięcie starszych wersji środowiska uruchomieniowego może zmienić środowisko uruchomieniowe wybrane do uruchamiania aplikacji platformy udostępnionej, zgodnie z opisem w artykule na temat [wyboru wersji platformy .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="01348-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="01348-106">Czy należy usunąć wersję?</span><span class="sxs-lookup"><span data-stu-id="01348-106">Should I remove a version?</span></span>

<span data-ttu-id="01348-107">Zachowania [wyboru wersji .NET Core](selection.md) i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwiają bezpieczne usuwanie poprzednich wersji.</span><span class="sxs-lookup"><span data-stu-id="01348-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="01348-108">Aktualizacje środowiska uruchomieniowego programu .NET Core są zgodne z wersją główną "Band", taką jak 1. x i 2. x.</span><span class="sxs-lookup"><span data-stu-id="01348-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="01348-109">Ponadto nowsze wersje zestaw .NET Core SDK zwykle utrzymują możliwość tworzenia aplikacji przeznaczonych dla wcześniejszych wersji środowiska uruchomieniowego w sposób zgodny.</span><span class="sxs-lookup"><span data-stu-id="01348-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="01348-110">Ogólnie rzecz biorąc potrzebny jest tylko najnowszy zestaw SDK i Najnowsza wersja poprawki środowiska uruchomieniowego, które są wymagane dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01348-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="01348-111">Wystąpienia, w których są zachowywane starsze wersje zestawu SDK lub środowiska uruchomieniowego, obejmują obsługę aplikacji opartych na **programie Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="01348-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="01348-112">Jeśli aplikacja nie ma określonych powodów dla wcześniejszych zestawów SDK lub środowisk uruchomieniowych, możesz bezpiecznie usunąć starsze wersje.</span><span class="sxs-lookup"><span data-stu-id="01348-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="01348-113">Określ, co jest zainstalowane</span><span class="sxs-lookup"><span data-stu-id="01348-113">Determine what is installed</span></span>

<span data-ttu-id="01348-114">Począwszy od platformy .NET Core 2,1, interfejs wiersza polecenia platformy .NET zawiera opcje, których można użyć do wyświetlenia listy wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="01348-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="01348-115">Użyj [`dotnet --list-sdks`](../tools/dotnet.md#options) , aby wyświetlić listę zestawów SDK zainstalowanych na maszynie.</span><span class="sxs-lookup"><span data-stu-id="01348-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="01348-116">Użyj [`dotnet --list-runtimes`](../tools/dotnet.md#options) , aby wyświetlić listę środowisk uruchomieniowych zainstalowanych na maszynie.</span><span class="sxs-lookup"><span data-stu-id="01348-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="01348-117">Poniższy tekst przedstawia typowe dane wyjściowe dla systemu Windows, macOS lub Linux:</span><span class="sxs-lookup"><span data-stu-id="01348-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="01348-118">Windows</span><span class="sxs-lookup"><span data-stu-id="01348-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="01348-119">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="01348-120">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-120">You get output similar to the following:</span></span>

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

<span data-ttu-id="01348-121">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="01348-122">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-122">You get output similar to the following:</span></span>

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

# <a name="linux"></a>[<span data-ttu-id="01348-123">Linux</span><span class="sxs-lookup"><span data-stu-id="01348-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="01348-124">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="01348-125">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-125">You get output similar to the following:</span></span>

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

<span data-ttu-id="01348-126">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="01348-127">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-127">You get output similar to the following:</span></span>

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

# <a name="macos"></a>[<span data-ttu-id="01348-128">macOS</span><span class="sxs-lookup"><span data-stu-id="01348-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="01348-129">Uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="01348-130">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-130">You get output similar to the following:</span></span>

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

<span data-ttu-id="01348-131">I uruchamiając następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="01348-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="01348-132">Dane wyjściowe są podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="01348-132">You get output similar to the following:</span></span>

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

## <a name="uninstall-net-core"></a><span data-ttu-id="01348-133">Odinstalowywanie programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="01348-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="01348-134">Windows</span><span class="sxs-lookup"><span data-stu-id="01348-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="01348-135">.NET Core używa okna dialogowego **Dodawanie/usuwanie programów** systemu Windows do usuwania wersji środowiska uruchomieniowego i zestawu SDK platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01348-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="01348-136">Na poniższej ilustracji przedstawiono okno dialogowe **Dodawanie/usuwanie programów** z kilkoma wersjami środowiska uruchomieniowego .NET i ZAINSTALOWANYm zestawem SDK.</span><span class="sxs-lookup"><span data-stu-id="01348-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Dodawanie/usuwanie programów w celu usunięcia programu .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="01348-138">Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="01348-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="01348-139">Linux</span><span class="sxs-lookup"><span data-stu-id="01348-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="01348-140">Istnieje więcej opcji odinstalowywania platformy .NET Core (zestawu SDK lub środowiska uruchomieniowego) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="01348-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="01348-141">Najlepszym sposobem odinstalowania programu .NET Core jest dublowanie akcji użytej do zainstalowania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="01348-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="01348-142">Informacje te zależą od wybranej dystrybucji i metody instalacji.</span><span class="sxs-lookup"><span data-stu-id="01348-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="01348-143">Aby uzyskać informacje na temat instalowania i odinstalowywania programu .NET Core, należy zapoznać się z [przewodnikiem](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) w witrynie red Hat wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="01348-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="01348-144">Począwszy od platformy .NET Core 2,1, nie ma potrzeby odinstalowywania zestaw .NET Core SDK podczas uaktualniania go przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="01348-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="01348-145">Polecenie `update` lub `refresh` Menedżera pakietów automatycznie usunie starszą wersję po pomyślnej instalacji nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="01348-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="01348-146">Jeśli zainstalowano program .NET Core przy użyciu Menedżera pakietów, należy użyć tego samego Menedżera pakietów do odinstalowania zestawu .NET SDK lub środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="01348-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="01348-147">Instalacje .NET Core obsługują najpopularniejszych menedżerów pakietów.</span><span class="sxs-lookup"><span data-stu-id="01348-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="01348-148">Zapoznaj się z dokumentacją Menedżera pakietów dystrybucji, aby uzyskać dokładną składnię w Twoim środowisku:</span><span class="sxs-lookup"><span data-stu-id="01348-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="01348-149">[apt-get (8)](https://linux.die.net/man/8/apt-get) jest używany przez systemy oparte na Debian, w tym Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="01348-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="01348-150">[yum (8)](https://linux.die.net/man/8/yum) jest używany na Fedora, CentOS i Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="01348-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="01348-151">[użyciu narzędzia zypper (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używany w systemach OPENSUSE i SUSE Linux Enterprise System (SLES).</span><span class="sxs-lookup"><span data-stu-id="01348-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="01348-152">[DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) jest używany w Fedora.</span><span class="sxs-lookup"><span data-stu-id="01348-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="01348-153">Niemal we wszystkich przypadkach polecenie usunięcia pakietu jest `remove`.</span><span class="sxs-lookup"><span data-stu-id="01348-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="01348-154">Nazwa pakietu dla zestaw .NET Core SDK instalacji większości menedżerów pakietów jest `dotnet-sdk`, a po niej numer wersji.</span><span class="sxs-lookup"><span data-stu-id="01348-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="01348-155">Począwszy od wersji 2.1.300 zestaw .NET Core SDK i wersji `2.1` środowiska uruchomieniowego, wymagane są tylko główne i pomocnicze numery wersji: na przykład zestaw .NET Core SDK wersja 2.1.300 może być przywoływana jako `dotnet-sdk-2.1`pakietu.</span><span class="sxs-lookup"><span data-stu-id="01348-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="01348-156">Wcześniejsze wersje wymagają całego ciągu wersji: na przykład, `dotnet-sdk-2.1.200` być wymagana dla wersji 2.1.200 zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="01348-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="01348-157">W przypadku maszyn, na których zainstalowano tylko środowisko uruchomieniowe, a nie zestawu SDK, nazwa pakietu jest `dotnet-runtime-<version>` dla środowiska uruchomieniowego .NET Core i `aspnetcore-runtime-<version>` dla całego stosu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="01348-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="01348-158">Instalacje .NET Core starsze niż 2,0 nie odinstalowały aplikacji hosta podczas odinstalowywania zestawu SDK przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="01348-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="01348-159">Przy użyciu `apt-get`polecenie to:</span><span class="sxs-lookup"><span data-stu-id="01348-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="01348-160">Należy zauważyć, że nie ma wersji dołączonej do `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="01348-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="01348-161">Jeśli zainstalowano program przy użyciu plik tar, należy usunąć platformę .NET Core przy użyciu metody ręcznej.</span><span class="sxs-lookup"><span data-stu-id="01348-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="01348-162">Zestawy SDK i środowiska uruchomieniowe należy usunąć oddzielnie, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="01348-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="01348-163">Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="01348-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="01348-164">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych polecenia `dotnet --list-sdks` i `dotnet --list-runtimes`, jak pokazano w wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="01348-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="01348-165">macOS</span><span class="sxs-lookup"><span data-stu-id="01348-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="01348-166">Na komputerach Mac należy osobno usunąć zestawy SDK i środowiska uruchomieniowe, usuwając katalog zawierający tę wersję.</span><span class="sxs-lookup"><span data-stu-id="01348-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="01348-167">Na przykład aby usunąć zestaw 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń bash:</span><span class="sxs-lookup"><span data-stu-id="01348-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="01348-168">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych polecenia `dotnet --list-sdks` i `dotnet --list-runtimes`, jak pokazano w wcześniejszej tabeli.</span><span class="sxs-lookup"><span data-stu-id="01348-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="01348-169">Narzędzie do dezinstalacji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="01348-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="01348-170">[Narzędzie do dezinstalacji programu .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umożliwia usuwanie zestawów SDK i środowisk uruchomieniowych platformy .NET Core z systemu.</span><span class="sxs-lookup"><span data-stu-id="01348-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="01348-171">Dostępna jest kolekcja opcji, aby określić, które wersje mają być odinstalowane.</span><span class="sxs-lookup"><span data-stu-id="01348-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="01348-172">Zależność programu Visual Studio od wersji zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="01348-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="01348-173">Przed dodaniem programu Visual Studio 2019 w wersji 16,3, instalatorzy programu Visual Studio o nazwie autonomiczne zestaw .NET Core SDK Instalatora.</span><span class="sxs-lookup"><span data-stu-id="01348-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="01348-174">W związku z tym wersje zestawu SDK pojawiają się w oknie dialogowym **Dodaj/Usuń programy** systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="01348-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="01348-175">Usunięcie zestawów SDK platformy .NET Core zainstalowanych przez program Visual Studio za pomocą autonomicznego Instalatora może spowodować przerwanie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="01348-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="01348-176">Jeśli program Visual Studio ma problemy po odinstalowaniu zestawów SDK, należy uruchomić polecenie Repair dla tej konkretnej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="01348-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="01348-177">W poniższej tabeli przedstawiono niektóre zależności programu Visual Studio na zestaw .NET Core SDK wersje:</span><span class="sxs-lookup"><span data-stu-id="01348-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="01348-178">Wersja programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="01348-178">Visual Studio version</span></span> | <span data-ttu-id="01348-179">Wersja zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="01348-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="01348-180">Visual Studio 2019 w wersji 16,2</span><span class="sxs-lookup"><span data-stu-id="01348-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="01348-181">Zestaw .NET Core SDK 2.2.4 XX, 2.1.8 XX</span><span class="sxs-lookup"><span data-stu-id="01348-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="01348-182">Visual Studio 2019 w wersji 16,1</span><span class="sxs-lookup"><span data-stu-id="01348-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="01348-183">Zestaw .NET Core SDK 2.2.3 XX, 2.1.7 XX</span><span class="sxs-lookup"><span data-stu-id="01348-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="01348-184">Visual Studio 2019 w wersji 16,0</span><span class="sxs-lookup"><span data-stu-id="01348-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="01348-185">Zestaw .NET Core SDK 2.2.2 XX, 2.1.6 XX</span><span class="sxs-lookup"><span data-stu-id="01348-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="01348-186">Visual Studio 2017 w wersji 15,9</span><span class="sxs-lookup"><span data-stu-id="01348-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="01348-187">Zestaw .NET Core SDK 2.2.1 XX, 2.1.5 XX</span><span class="sxs-lookup"><span data-stu-id="01348-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="01348-188">Visual Studio 2017 w wersji 15.8</span><span class="sxs-lookup"><span data-stu-id="01348-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="01348-189">Zestaw .NET Core SDK 2.1.4 XX</span><span class="sxs-lookup"><span data-stu-id="01348-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="01348-190">Począwszy od programu Visual Studio 2019 w wersji 16,3, program Visual Studio jest odpowiedzialny za własną kopię zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="01348-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="01348-191">Z tego powodu nie widzisz już tych wersji zestawu SDK w oknie dialogowym **Dodaj/Usuń programy** .</span><span class="sxs-lookup"><span data-stu-id="01348-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="01348-192">Usuń folder rezerwowy NuGet</span><span class="sxs-lookup"><span data-stu-id="01348-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="01348-193">Przed zestawem SDK platformy .NET Core 3,0, instalatorzy zestaw .NET Core SDK używają *NuGetFallbackFolder* do przechowywania pamięci podręcznej pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="01348-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="01348-194">Ta pamięć podręczna została użyta podczas operacji takich jak `dotnet restore` lub `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="01348-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="01348-195">`NuGetFallbackFolder` znajduje się w *katalogu C:\Program Files\dotnet\sdk* w systemie Windows i w */usr/local/share/dotnet/SDK* na macOS.</span><span class="sxs-lookup"><span data-stu-id="01348-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="01348-196">Możesz chcieć usunąć ten folder, jeśli:</span><span class="sxs-lookup"><span data-stu-id="01348-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="01348-197">Program jest opracowywany tylko przy użyciu zestawu .NET Core 3,0 SDK lub jego nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="01348-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="01348-198">Opracowujesz program przy użyciu wersji zestaw .NET Core SDK wcześniejszej niż 3,0, ale możesz pracować w trybie online, a rzeczy mogą przebiegać wolniej.</span><span class="sxs-lookup"><span data-stu-id="01348-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="01348-199">Jeśli chcesz usunąć folder rezerwowy NuGet, możesz go usunąć, ale musisz mieć uprawnienia administratora.</span><span class="sxs-lookup"><span data-stu-id="01348-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="01348-200">Nie zaleca się usuwania folderu *dotnet* .</span><span class="sxs-lookup"><span data-stu-id="01348-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="01348-201">Spowoduje to usunięcie wszystkich wcześniej zainstalowanych narzędzi globalnych.</span><span class="sxs-lookup"><span data-stu-id="01348-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="01348-202">Ponadto w systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="01348-202">Also, on Windows:</span></span>

- <span data-ttu-id="01348-203">Spowoduje to przerwanie programu Visual Studio 2019 w wersji 16,3 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="01348-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="01348-204">Aby odzyskać, możesz wykonać **naprawę** .</span><span class="sxs-lookup"><span data-stu-id="01348-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="01348-205">Jeśli w oknie dialogowym **Dodaj/Usuń programy** znajdują się zestaw .NET Core SDK wpisy, zostaną one oddzielone.</span><span class="sxs-lookup"><span data-stu-id="01348-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
