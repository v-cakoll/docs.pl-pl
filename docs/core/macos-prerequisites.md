---
title: Wymagania wstępne dla platformy .NET Core w systemie Mac
description: Obsługiwane wersje systemu macOS i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem macOS.
author: guardrex
ms.author: adegeo
ms.date: 12/14/2018
ms.openlocfilehash: bc6e0b20c61c474c7069b757528dbc1ea38354e3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656313"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="9baab-103">Wymagania wstępne dla platformy .NET Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="9baab-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="9baab-104">W tym artykule przedstawiono macOS obsługiwane wersje i zależności platformy .NET Core, umożliwiające tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="9baab-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="9baab-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby związanych z tworzeniem aplikacji .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia za pomocą ulubionego edytora](tutorials/using-with-xplat-cli.md), [programu Visual Studio Code](https://code.visualstudio.com/)i [Programu visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="9baab-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="9baab-106">Obsługiwane w systemie macOS w wersji</span><span class="sxs-lookup"><span data-stu-id="9baab-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9baab-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="9baab-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="9baab-108">.NET core 2.x jest obsługiwane w następujących wersji systemu MacOS:</span><span class="sxs-lookup"><span data-stu-id="9baab-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="9baab-109">System macOS 10.12 "Sierra" i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="9baab-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="9baab-110">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego platformy .NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) pełną listę platformy .NET Core 2.1 i .NET Core 2.2 obsługiwane systemy operacyjne, dystrybucji i wersji, z obsługuje wersje systemów operacyjnych i łącza zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="9baab-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="9baab-111">Łącza pobierania oraz więcej informacji, zobacz [platformy .NET Core 2.2 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.2) lub [platformy .NET Core 2.1 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="9baab-111">For download links and more information, see [.NET Core 2.2 downloads](https://www.microsoft.com/net/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://www.microsoft.com/net/download/dotnet-core/2.1).</span></span>


# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9baab-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9baab-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9baab-113">.NET core 1.x jest obsługiwane w następujących wersji systemu MacOS:</span><span class="sxs-lookup"><span data-stu-id="9baab-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="9baab-114">System macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="9baab-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="9baab-115">System macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="9baab-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="9baab-116">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 1.1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) i [obsługiwane wersje systemu operacyjnego platformy .NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pełną listę .NET Core 1.1 i platformy .NET Core 1.0 obsługiwane systemy operacyjne, dystrybucji i wersji, z obsługuje wersje systemów operacyjnych i łącza zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="9baab-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="9baab-117">Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET Core 1.1](https://www.microsoft.com/net/download/dotnet-core/1.1) lub [platformy .NET Core 1.0 pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="9baab-117">For download links and more information, see [.NET Core 1.1 downloads](https://www.microsoft.com/net/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://www.microsoft.com/net/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="9baab-118">.NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="9baab-118">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="9baab-119">.NET core 3.0 w wersji zapoznawczej 1 jest obsługiwane w następujących wersji systemu MacOS:</span><span class="sxs-lookup"><span data-stu-id="9baab-119">.NET Core 3.0 Preview 1 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="9baab-120">System macOS 10.12 "Sierra" i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="9baab-120">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="9baab-121">Zobacz [obsługiwane wersje systemu operacyjnego platformy .NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) .NET Core 3.0 to pełna lista obsługiwanych systemów operacyjnych, dystrybucji i wersji poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="9baab-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="9baab-122">Łącza pobierania oraz więcej informacji, zobacz [.NET Core 3.0 to pliki do pobrania](https://www.microsoft.com/net/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="9baab-122">For download links and more information, see [.NET Core 3.0 downloads](https://www.microsoft.com/net/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="9baab-123">Zależności platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="9baab-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="9baab-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="9baab-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="9baab-125">Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="9baab-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="9baab-126">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [znane problemy dotyczące](https://github.com/dotnet/core/tree/master/release-notes/2.1) temacie zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="9baab-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="9baab-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="9baab-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="9baab-128">.NET core 1.x wymaga biblioteki OpenSSL, podczas uruchamiania w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="9baab-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="9baab-129">Łatwym sposobem uzyskiwania OpenSSL polega na użyciu [Homebrew ("brew")](https://brew.sh/) Menedżer pakietów dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="9baab-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="9baab-130">Po zainstalowaniu *brew*, zainstalować protokół OpenSSL, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="9baab-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="9baab-131">Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="9baab-131">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="9baab-132">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 — znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="9baab-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30-preview-1tabnetcore30"></a>[<span data-ttu-id="9baab-133">.NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="9baab-133">.NET Core 3.0 Preview 1</span></span>](#tab/netcore30)

<span data-ttu-id="9baab-134">Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="9baab-134">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="9baab-135">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [informacje o wersji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) temacie zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="9baab-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="9baab-136">Zwiększ limit maksymalny otwartego pliku (wersje platformy .NET Core przed zestawu .NET Core SDK pkt 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="9baab-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="9baab-137">W starszych wersjach platformy .NET Core (przed zestawu .NET Core SDK pkt 2.0.2) domyślny limit Otwórz plik w systemie macOS może nie być wystarczające dla niektórych obciążeń platformy .NET Core, takich jak przywracanie projektów lub Uruchamianie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="9baab-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="9baab-138">Aby zwiększyć ten limit, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9baab-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="9baab-139">Za pomocą edytora tekstu Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_, a następnie zapisz plik z tą zawartością:</span><span class="sxs-lookup"><span data-stu-id="9baab-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN"
        "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. <span data-ttu-id="9baab-140">W oknie terminala uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9baab-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="9baab-141">Ponowny rozruch komputera Mac, aby zastosować te ustawienia.</span><span class="sxs-lookup"><span data-stu-id="9baab-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="9baab-142">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="9baab-142">Visual Studio for Mac</span></span>

<span data-ttu-id="9baab-143">Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="9baab-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="9baab-144">Jednakże, jeśli chcesz tworzyć aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, można użyć [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="9baab-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="9baab-145">Programowanie aplikacji platformy .NET core w systemie macOS przy użyciu programu Visual Studio for Mac wymaga:</span><span class="sxs-lookup"><span data-stu-id="9baab-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="9baab-146">Obsługiwana wersja systemu operacyjnego z systemem macOS</span><span class="sxs-lookup"><span data-stu-id="9baab-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="9baab-147">Biblioteki OpenSSL (.NET Core 1.x tylko; .NET Core 2.x używa zabezpieczeń usług dostępnych natywnie w systemie macOS)</span><span class="sxs-lookup"><span data-stu-id="9baab-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="9baab-148">.NET core SDK dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="9baab-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="9baab-149">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="9baab-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
