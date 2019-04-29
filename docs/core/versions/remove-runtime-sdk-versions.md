---
title: Usuń środowisko uruchomieniowe programu .NET Core i zestawu SDK
description: W tym artykule opisano sposób określania, które wersje środowiska uruchomieniowego programu .NET Core i zestawu SDK są zainstalowane, a następnie jak je usunąć w Windows, Mac i Linux.
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.custom: seodec18
ms.openlocfilehash: 4e336abf62299e0dee2e4757bb83f967ed4aed59
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646897"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="bd817-103">Jak usunąć środowisko uruchomieniowe programu .NET Core i zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="bd817-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="bd817-104">Wraz z upływem czasu jak zainstalować zaktualizowane wersje środowiska uruchomieniowego .NET Core i zestawu SDK, warto Usuń nieaktualne wersje programu .NET Core z poziomu Twojej maszyny.</span><span class="sxs-lookup"><span data-stu-id="bd817-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="bd817-105">Trwa usuwanie starszych wersji środowiska uruchomieniowego mogą ulec zmianie środowiska uruchomieniowego, wybierany do uruchamiania aplikacji udostępnionej platformy, zgodnie z opisem w artykule na [wybór wersji platformy .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="bd817-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="bd817-106">Czy należy usunąć wersję?</span><span class="sxs-lookup"><span data-stu-id="bd817-106">Should I remove a version?</span></span>

<span data-ttu-id="bd817-107">[Wybór wersji platformy .NET Core](selection.md) zachowań i zgodność środowiska uruchomieniowego programu .NET Core między aktualizacjami umożliwia bezpieczne usuwanie wcześniejszych wersji.</span><span class="sxs-lookup"><span data-stu-id="bd817-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="bd817-108">Aktualizacje środowiska uruchomieniowego .NET core są zgodne w ramach wersji głównej "pasma, takich jak wersji 1.x i 2.x.</span><span class="sxs-lookup"><span data-stu-id="bd817-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="bd817-109">Ponadto nowsze wersje programu .NET Core SDK zazwyczaj zachować możliwość tworzenia aplikacji w tym docelowymi są poprzednie wersje środowiska uruchomieniowego w sposób zgodny.</span><span class="sxs-lookup"><span data-stu-id="bd817-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="bd817-110">Ogólnie rzecz biorąc wystarczy tylko najnowszy zestaw SDK i najnowszą wersję poprawki środowisk uruchomieniowych wymagane dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd817-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="bd817-111">Wystąpienia, których przechowywanie starsze wersje zestawu SDK lub środowiska uruchomieniowego obejmują ochronną **project.json**— na podstawie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd817-111">Instances where retaining older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="bd817-112">Jeśli aplikacja ma określone przyczyny, dla starszych zestawów SDK lub środowisk wykonawczych, możesz bezpiecznie usunąć starsze wersje.</span><span class="sxs-lookup"><span data-stu-id="bd817-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="bd817-113">Określić, co jest zainstalowana</span><span class="sxs-lookup"><span data-stu-id="bd817-113">Determine what is installed</span></span>

<span data-ttu-id="bd817-114">Począwszy od platformy .NET Core 2.1 interfejsu wiersza polecenia platformy .NET zawiera opcje, których można użyć, aby wyświetlić listę wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="bd817-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="bd817-115">Użyj [ `dotnet --list-sdks` ](../tools/dotnet.md#options) Aby wyświetlić listę zestawów SDK zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bd817-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="bd817-116">Użyj [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) Aby wyświetlić listę środowiska uruchomieniowe zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="bd817-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="bd817-117">Następujący tekst przedstawiono typowe dane wyjściowe, Windows, macOS i Linux:</span><span class="sxs-lookup"><span data-stu-id="bd817-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="bd817-118">Windows</span><span class="sxs-lookup"><span data-stu-id="bd817-118">Windows</span></span>](#tab/windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="bd817-119">Linux</span><span class="sxs-lookup"><span data-stu-id="bd817-119">Linux</span></span>](#tab/linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="bd817-120">macOS</span><span class="sxs-lookup"><span data-stu-id="bd817-120">macOS</span></span>](#tab/macos)

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

## <a name="uninstalling-net-core"></a><span data-ttu-id="bd817-121">Odinstalowywanie platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd817-121">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="bd817-122">Windows</span><span class="sxs-lookup"><span data-stu-id="bd817-122">Windows</span></span>](#tab/windows)

<span data-ttu-id="bd817-123">Windows korzysta z platformy .NET core **Dodaj/Usuń programy** okno dialogowe, aby usunąć wersje środowiska uruchomieniowego .NET Core i zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="bd817-123">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="bd817-124">Poniższy rysunek przedstawia **Dodaj/Usuń programy** okna dialogowego z różnymi wersjami środowiska uruchomieniowego .NET i zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="bd817-124">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Dodaj / Usuń programy, aby usunąć .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="bd817-126">Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="bd817-126">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="bd817-127">Linux</span><span class="sxs-lookup"><span data-stu-id="bd817-127">Linux</span></span>](#tab/linux)

<span data-ttu-id="bd817-128">Istnieje więcej opcji, aby odinstalować platformy .NET Core (zestaw SDK lub środowisko uruchomieniowe) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="bd817-128">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="bd817-129">Najlepszym sposobem odinstalować platformy .NET Core jest duplikatów akcję, która umożliwia instalowanie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd817-129">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="bd817-130">Szczegółowe informacje na temat, zależy od wybranej dystrybucji i metody instalacji.</span><span class="sxs-lookup"><span data-stu-id="bd817-130">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd817-131">W przypadku instalacji Red Hat, zapoznaj się z [Red Hat — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) instrukcje dotyczące instalowania i odinstalowywania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd817-131">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="bd817-132">Począwszy od platformy .NET Core 2.1 nie ma potrzeby odinstalowania zestawu .NET Core SDK, podczas uaktualniania go przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="bd817-132">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="bd817-133">Menedżer pakietów `update` lub `refresh` polecenia spowoduje automatyczne usunięcie starszej wersji po pomyślnej instalacji w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="bd817-133">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="bd817-134">Po zainstalowaniu platformy .NET Core przy użyciu Menedżera pakietów, użyjesz tej samej Menedżera pakietów odinstalować zestaw SDK platformy .NET lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="bd817-134">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="bd817-135">Instalacje .NET core obsługuje najbardziej popularne Menedżery pakietów.</span><span class="sxs-lookup"><span data-stu-id="bd817-135">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="bd817-136">Zapoznaj się z dokumentacją dla Twojej dystrybucji Menedżer pakietów dla dokładne składni w swoim środowisku:</span><span class="sxs-lookup"><span data-stu-id="bd817-136">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="bd817-137">[apt-GET(8)](https://linux.die.net/man/8/apt-get) jest używany przez Debian systemów, w tym Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="bd817-137">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="bd817-138">[YUM(8)](https://linux.die.net/man/8/yum) jest używana na Fedora i CentOS, Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="bd817-138">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="bd817-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używana w systemach openSUSE i SUSE Linux Enterprise systemu (SLES).</span><span class="sxs-lookup"><span data-stu-id="bd817-139">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="bd817-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) na Fedora ma być używana.</span><span class="sxs-lookup"><span data-stu-id="bd817-140">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="bd817-141">W większości przypadków, to polecenie, aby usunąć pakiet `remove`.</span><span class="sxs-lookup"><span data-stu-id="bd817-141">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="bd817-142">Nazwa pakietu dla większości menedżerów pakietów instalacji zestawu .NET Core SDK jest `dotnet-sdk`, a następnie za pomocą numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="bd817-142">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="bd817-143">Począwszy od wersji 2.1.300 zestawu .NET Core SDK, a wersja `2.1` środowiska uruchomieniowego, wymagane są tylko numery wersji głównych i pomocniczych: na przykład, .NET Core SDK w wersji 2.1.300 mogą być przywoływane w taki sposób, jak pakiet `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="bd817-143">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="bd817-144">Wcześniejsze wersje wymagają całą wersję ciągu: na przykład `dotnet-sdk-2.1.200` jest wymagana dla wersji 2.1.200 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="bd817-144">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="bd817-145">Dla maszyn, na których zainstalowano tylko środowiska uruchomieniowego, a nie zestaw SDK, pakiet nazywa `dotnet-runtime-<version>` dla środowiska uruchomieniowego .NET Core, i `aspnetcore-runtime-<version>` dla stosu całego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bd817-145">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="bd817-146">Instalacje .NET core 2.0 — przed odinstalowaniem aplikacji hosta odinstalowanie zestawu SDK przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="bd817-146">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="bd817-147">Za pomocą `apt-get`, polecenie to:</span><span class="sxs-lookup"><span data-stu-id="bd817-147">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="bd817-148">Należy zauważyć, że wersja nie jest dołączony do `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="bd817-148">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="bd817-149">Jeśli został zainstalowany przy użyciu pliku tar, należy usunąć .NET Core przy użyciu metody ręcznej.</span><span class="sxs-lookup"><span data-stu-id="bd817-149">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="bd817-150">Możesz usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, przez usunięcie katalogu, który zawiera tę wersję.</span><span class="sxs-lookup"><span data-stu-id="bd817-150">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="bd817-151">Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:</span><span class="sxs-lookup"><span data-stu-id="bd817-151">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="bd817-152">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bd817-152">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="bd817-153">macOS</span><span class="sxs-lookup"><span data-stu-id="bd817-153">macOS</span></span>](#tab/macos)

<span data-ttu-id="bd817-154">Na komputerze Mac należy usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, usuwając katalogu, który zawiera tę wersję.</span><span class="sxs-lookup"><span data-stu-id="bd817-154">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="bd817-155">Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:</span><span class="sxs-lookup"><span data-stu-id="bd817-155">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="bd817-156">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.</span><span class="sxs-lookup"><span data-stu-id="bd817-156">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---
