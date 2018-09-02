---
title: Jak usunąć środowisko uruchomieniowe platformy .NET i zestawu SDK
description: Instrukcje dotyczące usuwania składników środowiska uruchomieniowego programu .NET Core i zestawu SDK w Windows, Mac i Linux
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409146"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="d9d9b-103">Jak usunąć środowisko uruchomieniowe programu .NET Core i zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="d9d9b-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="d9d9b-104">Wraz z upływem czasu jak zainstalować zaktualizowane wersje środowiska uruchomieniowego .NET Core i zestawu SDK, warto Usuń nieaktualne wersje programu .NET Core z poziomu Twojej maszyny.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="d9d9b-105">Trwa usuwanie starszych wersji środowiska uruchomieniowego mogą ulec zmianie środowiska uruchomieniowego, wybierany do uruchamiania aplikacji udostępnionej platformy, zgodnie z opisem w artykule na [wybór wersji platformy .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="d9d9b-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="d9d9b-106">Począwszy od platformy .NET Core 2.1 interfejsu wiersza polecenia platformy .NET zawiera opcje, których można użyć, aby wyświetlić listę wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-106">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="d9d9b-107">Użyj [ `dotnet --list-sdks` ](../tools/dotnet.md#options) Aby wyświetlić listę zestawów SDK zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="d9d9b-108">Użyj [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) Aby wyświetlić listę środowiska uruchomieniowe zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="d9d9b-109">Następujący tekst przedstawiono typowe dane wyjściowe, Windows, macOS i Linux:</span><span class="sxs-lookup"><span data-stu-id="d9d9b-109">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="d9d9b-110">Windows</span><span class="sxs-lookup"><span data-stu-id="d9d9b-110">Windows</span></span>](#tab/Windows)

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

# <a name="linuxtablinux"></a>[<span data-ttu-id="d9d9b-111">Linux</span><span class="sxs-lookup"><span data-stu-id="d9d9b-111">Linux</span></span>](#tab/Linux)

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

# <a name="macostabmacos"></a>[<span data-ttu-id="d9d9b-112">macOS</span><span class="sxs-lookup"><span data-stu-id="d9d9b-112">macOS</span></span>](#tab/macOS)

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

***

## <a name="uninstalling-net-core"></a><span data-ttu-id="d9d9b-113">Odinstalowywanie platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9d9b-113">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="d9d9b-114">Windows</span><span class="sxs-lookup"><span data-stu-id="d9d9b-114">Windows</span></span>](#tab/Windows)

<span data-ttu-id="d9d9b-115">Windows korzysta z platformy .NET core **Dodaj/Usuń programy** okno dialogowe, aby usunąć wersje środowiska uruchomieniowego .NET Core i zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-115">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="d9d9b-116">Poniższy rysunek przedstawia **Dodaj/Usuń programy** okna dialogowego z różnymi wersjami środowiska uruchomieniowego .NET i zainstalowany zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-116">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Dodaj / Usuń programy, aby usunąć .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="d9d9b-118">Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-118">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="d9d9b-119">Linux</span><span class="sxs-lookup"><span data-stu-id="d9d9b-119">Linux</span></span>](#tab/Linux)

<span data-ttu-id="d9d9b-120">Istnieje więcej opcji, aby odinstalować platformy .NET Core (zestaw SDK lub środowisko uruchomieniowe) w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-120">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="d9d9b-121">Najlepszym sposobem odinstalować platformy .NET Core jest duplikatów akcję, która umożliwia instalowanie programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-121">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="d9d9b-122">Szczegółowe informacje na temat, zależy od wybranej dystrybucji i metody instalacji.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-122">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d9d9b-123">W przypadku instalacji Red Hat, zapoznaj się z [Red Hat — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) instrukcje dotyczące instalowania i odinstalowywania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-123">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="d9d9b-124">Począwszy od platformy .NET Core 2.1 nie ma potrzeby odinstalowania zestawu .NET Core SDK, podczas uaktualniania go przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-124">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="d9d9b-125">Menedżer pakietów `update` lub `refresh` polecenia spowoduje automatyczne usunięcie starszej wersji po pomyślnej instalacji w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-125">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="d9d9b-126">Po zainstalowaniu platformy .NET Core przy użyciu Menedżera pakietów, użyjesz tej samej Menedżera pakietów odinstalować zestaw SDK platformy .NET lub środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-126">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="d9d9b-127">Instalacje .NET core obsługuje najbardziej popularne Menedżery pakietów.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-127">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="d9d9b-128">Zapoznaj się z dokumentacją dla Twojej dystrybucji Menedżer pakietów dla dokładne składni w swoim środowisku:</span><span class="sxs-lookup"><span data-stu-id="d9d9b-128">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="d9d9b-129">[apt-GET(8)](https://linux.die.net/man/8/apt-get) jest używany przez Debian systemów, w tym Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="d9d9b-130">[YUM(8)](https://linux.die.net/man/8/yum) jest używana na Fedora i CentOS, Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-130">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="d9d9b-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używana w systemach openSUSE i SUSE Linux Enterprise systemu (SLES).</span><span class="sxs-lookup"><span data-stu-id="d9d9b-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="d9d9b-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) na Fedora ma być używana.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="d9d9b-133">W większości przypadków, to polecenie, aby usunąć pakiet `remove`.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-133">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="d9d9b-134">Nazwa pakietu dla większości menedżerów pakietów instalacji zestawu .NET Core SDK jest `dotnet-sdk`, a następnie za pomocą numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-134">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="d9d9b-135">Począwszy od wersji 2.1.300 zestawu .NET Core SDK, a wersja `2.1` środowiska uruchomieniowego, wymagane są tylko numery wersji głównych i pomocniczych: na przykład, .NET Core SDK w wersji 2.1.300 mogą być przywoływane w taki sposób, jak pakiet `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-135">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="d9d9b-136">Wcześniejsze wersje wymagają całą wersję ciągu: na przykład `dotnet-sdk-2.1.200` jest wymagana dla wersji 2.1.200 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-136">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="d9d9b-137">Dla maszyn, na których zainstalowano tylko środowiska uruchomieniowego, a nie zestaw SDK, pakiet nazywa `dotnet-runtime-<version>` dla środowiska uruchomieniowego .NET Core, i `aspnetcore-runtime-<version>` dla stosu całego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-137">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="d9d9b-138">Instalacje .NET core 2.0 — przed odinstalowaniem aplikacji hosta odinstalowanie zestawu SDK przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-138">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="d9d9b-139">Za pomocą `apt-get`, polecenie to:</span><span class="sxs-lookup"><span data-stu-id="d9d9b-139">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="d9d9b-140">Należy zauważyć, że wersja nie jest dołączony do `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-140">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="d9d9b-141">Jeśli został zainstalowany przy użyciu pliku tar, należy usunąć .NET Core przy użyciu metody ręcznej.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-141">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="d9d9b-142">Możesz usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, przez usunięcie katalogu, który zawiera tę wersję.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-142">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="d9d9b-143">Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:</span><span class="sxs-lookup"><span data-stu-id="d9d9b-143">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="d9d9b-144">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-144">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="d9d9b-145">macOS</span><span class="sxs-lookup"><span data-stu-id="d9d9b-145">macOS</span></span>](#tab/macOS)

<span data-ttu-id="d9d9b-146">Na komputerze Mac należy usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, usuwając katalogu, który zawiera tę wersję.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-146">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="d9d9b-147">Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:</span><span class="sxs-lookup"><span data-stu-id="d9d9b-147">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="d9d9b-148">Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-148">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

<span data-ttu-id="d9d9b-149">Począwszy od platformy .NET Core 2.1 nie ma potrzeby odinstalowania zestawu .NET Core SDK, podczas uaktualniania go przy użyciu Menedżera pakietów.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-149">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="d9d9b-150">Menedżer pakietów `update` lub `refresh` polecenia spowoduje automatyczne usunięcie starszej wersji po pomyślnej instalacji w nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="d9d9b-150">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

---
