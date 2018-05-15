---
title: Wymagania wstępne dotyczące platformy .NET Core dla komputerów Mac
description: Obsługiwane wersje macOS i zależności platformy .NET Core na tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach macOS.
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.openlocfilehash: b1f4d3b49be7ba5349197187d6576b78db58798c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="47c55-103">Wymagania wstępne dotyczące .NET Core na macOS</span><span class="sxs-lookup"><span data-stu-id="47c55-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="47c55-104">W tym artykule przedstawiono macOS obsługiwane wersje i zależności platformy .NET Core, umożliwiające tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach macOS.</span><span class="sxs-lookup"><span data-stu-id="47c55-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="47c55-105">Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionego edytora](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Programu visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="47c55-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="47c55-106">System macOS obsługiwane wersje</span><span class="sxs-lookup"><span data-stu-id="47c55-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="47c55-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="47c55-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="47c55-108">Oprogramowanie .NET core 2.x jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="47c55-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="47c55-109">System macOS 10.12 "Sierra" i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="47c55-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="47c55-110">Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="47c55-110">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="47c55-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="47c55-111">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="47c55-112">Oprogramowanie .NET core 1.x jest obsługiwana w następujących wersjach macOS:</span><span class="sxs-lookup"><span data-stu-id="47c55-112">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="47c55-113">System macOS 10.12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="47c55-113">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="47c55-114">System macOS 10.11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="47c55-114">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="47c55-115">Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) Pełna lista .NET Core 1.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="47c55-115">See [.NET Core 1.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="47c55-116">Zależności .NET core</span><span class="sxs-lookup"><span data-stu-id="47c55-116">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="47c55-117">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="47c55-117">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="47c55-118">Pobierz i zainstaluj .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="47c55-118">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="47c55-119">Jeśli masz problemy z instalacją na macOS, należy skontaktować się [znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tematu zainstalowaną wersję.</span><span class="sxs-lookup"><span data-stu-id="47c55-119">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.0) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="47c55-120">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="47c55-120">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="47c55-121">**.NET Core 1.x**</span><span class="sxs-lookup"><span data-stu-id="47c55-121">**.NET Core 1.x**</span></span>

<span data-ttu-id="47c55-122">Oprogramowanie .NET core 1.x wymaga biblioteki OpenSSL, podczas uruchamiania na macOS.</span><span class="sxs-lookup"><span data-stu-id="47c55-122">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="47c55-123">Jest łatwy sposób uzyskać biblioteki OpenSSL przy użyciu [Homebrew ("brew")](https://brew.sh/) Menedżer pakietów dla macOS.</span><span class="sxs-lookup"><span data-stu-id="47c55-123">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="47c55-124">Po zainstalowaniu *brew*, zainstaluj biblioteki OpenSSL, wykonując następujące polecenia w wierszu terminali (polecenie):</span><span class="sxs-lookup"><span data-stu-id="47c55-124">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="47c55-125">Pobierz i zainstaluj .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="47c55-125">Download and install the .NET Core SDK from [.NET Downloads](https://www.microsoft.com/net/download/core).</span></span> <span data-ttu-id="47c55-126">Jeśli masz problemy z instalacją na macOS, należy skontaktować się [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematów.</span><span class="sxs-lookup"><span data-stu-id="47c55-126">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="47c55-127">Zwiększ limit maksymalnego Otwórz plik (wersje .NET Core przed .NET Core SDK pkt 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="47c55-127">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span> 

<span data-ttu-id="47c55-128">W starszych wersjach platformy .NET Core (przed .NET Core SDK pkt 2.0.2) domyślny limit Otwórz plik na macOS nie może być wystarczające dla niektórych obciążeń .NET Core, takich jak przywracanie projektów lub przeprowadzanie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="47c55-128">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="47c55-129">Aby zwiększyć ten limit, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="47c55-129">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="47c55-130">Za pomocą edytora tekstu, Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_i Zapisz plik z tą zawartością:</span><span class="sxs-lookup"><span data-stu-id="47c55-130">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

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

2. <span data-ttu-id="47c55-131">W oknie terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="47c55-131">In a terminal window, run the following command:</span></span>

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. <span data-ttu-id="47c55-132">Ponowny rozruch komputera Mac, aby zastosować te ustawienia.</span><span class="sxs-lookup"><span data-stu-id="47c55-132">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="47c55-133">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="47c55-133">Visual Studio for Mac</span></span>

<span data-ttu-id="47c55-134">Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora.</span><span class="sxs-lookup"><span data-stu-id="47c55-134">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="47c55-135">Jednak jeśli chcesz wdrażać aplikacje .NET Core na komputerze Mac w zintegrowane środowisko programistyczne, można użyć [programu Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span><span class="sxs-lookup"><span data-stu-id="47c55-135">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).</span></span> 

<span data-ttu-id="47c55-136">Tworzenie aplikacji platformy .NET core na macOS z programem Visual Studio for Mac wymaga:</span><span class="sxs-lookup"><span data-stu-id="47c55-136">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="47c55-137">Obsługiwana wersja systemu operacyjnego macOS</span><span class="sxs-lookup"><span data-stu-id="47c55-137">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="47c55-138">Biblioteki OpenSSL (.NET Core 1.x tylko; dostępna natywnie w macOS usług zabezpieczeń używa 2.x .NET Core)</span><span class="sxs-lookup"><span data-stu-id="47c55-138">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="47c55-139">Oprogramowanie .NET core SDK dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="47c55-139">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="47c55-140">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="47c55-140">Visual Studio for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)
