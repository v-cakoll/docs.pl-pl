---
title: Wymagania wstępne dla platformy .NET Core w systemie Mac
description: Obsługiwane wersje systemu macOS i zależności platformy .NET Core, opracowywanie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem macOS.
author: guardrex
ms.author: mairaw
ms.date: 10/03/2018
ms.openlocfilehash: b5b3c6ea90a2cc4487e849af468d324b645834af
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48584081"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="270cb-103">Wymagania wstępne dla platformy .NET Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="270cb-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="270cb-104">W tym artykule przedstawiono macOS obsługiwane wersje i zależności platformy .NET Core, umożliwiające tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem macOS.</span><span class="sxs-lookup"><span data-stu-id="270cb-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="270cb-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby związanych z tworzeniem aplikacji .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia za pomocą ulubionego edytora](tutorials/using-with-xplat-cli.md), [programu Visual Studio Code](https://code.visualstudio.com/)i [Programu visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="270cb-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="270cb-106">Obsługiwane w systemie macOS w wersji</span><span class="sxs-lookup"><span data-stu-id="270cb-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="270cb-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="270cb-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="270cb-108">.NET core 2.x jest obsługiwane w następujących wersji systemu MacOS:</span><span class="sxs-lookup"><span data-stu-id="270cb-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="270cb-109">System macOS 10.12 "Sierra" i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="270cb-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="270cb-110">Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) kompletną listę platformy .NET Core 2.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="270cb-110">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="270cb-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="270cb-111">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="270cb-112">.NET core 1.x jest obsługiwane w następujących wersji systemu MacOS:</span><span class="sxs-lookup"><span data-stu-id="270cb-112">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="270cb-113">System macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="270cb-113">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="270cb-114">System macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="270cb-114">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="270cb-115">Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="270cb-115">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="270cb-116">Zależności platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="270cb-116">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="270cb-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="270cb-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="270cb-118">Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="270cb-118">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="270cb-119">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [znane problemy dotyczące](https://github.com/dotnet/core/tree/master/release-notes/2.1) temacie zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="270cb-119">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="270cb-120">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="270cb-120">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="270cb-121">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="270cb-121">**.NET Core 1.x**</span></span>

<span data-ttu-id="270cb-122">.NET core 1.x wymaga biblioteki OpenSSL, podczas uruchamiania w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="270cb-122">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="270cb-123">Łatwym sposobem uzyskiwania OpenSSL polega na użyciu [Homebrew ("brew")](https://brew.sh/) Menedżer pakietów dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="270cb-123">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="270cb-124">Po zainstalowaniu *brew*, zainstalować protokół OpenSSL, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="270cb-124">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="270cb-125">Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="270cb-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="270cb-126">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 — znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="270cb-126">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="270cb-127">Zwiększ limit maksymalny otwartego pliku (wersje platformy .NET Core przed zestawu .NET Core SDK pkt 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="270cb-127">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="270cb-128">W starszych wersjach platformy .NET Core (przed zestawu .NET Core SDK pkt 2.0.2) domyślny limit Otwórz plik w systemie macOS może nie być wystarczające dla niektórych obciążeń platformy .NET Core, takich jak przywracanie projektów lub Uruchamianie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="270cb-128">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="270cb-129">Aby zwiększyć ten limit, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="270cb-129">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="270cb-130">Za pomocą edytora tekstu Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_, a następnie zapisz plik z tą zawartością:</span><span class="sxs-lookup"><span data-stu-id="270cb-130">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="270cb-131">W oknie terminala uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="270cb-131">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="270cb-132">Ponowny rozruch komputera Mac, aby zastosować te ustawienia.</span><span class="sxs-lookup"><span data-stu-id="270cb-132">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="270cb-133">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="270cb-133">Visual Studio for Mac</span></span>

<span data-ttu-id="270cb-134">Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="270cb-134">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="270cb-135">Jednakże, jeśli chcesz tworzyć aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, można użyć [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="270cb-135">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="270cb-136">Programowanie aplikacji platformy .NET core w systemie macOS przy użyciu programu Visual Studio for Mac wymaga:</span><span class="sxs-lookup"><span data-stu-id="270cb-136">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="270cb-137">Obsługiwana wersja systemu operacyjnego z systemem macOS</span><span class="sxs-lookup"><span data-stu-id="270cb-137">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="270cb-138">Biblioteki OpenSSL (.NET Core 1.x tylko; .NET Core 2.x używa zabezpieczeń usług dostępnych natywnie w systemie macOS)</span><span class="sxs-lookup"><span data-stu-id="270cb-138">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="270cb-139">.NET core SDK dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="270cb-139">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="270cb-140">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="270cb-140">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
