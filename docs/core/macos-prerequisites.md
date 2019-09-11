---
title: Wymagania wstępne dotyczące platformy .NET Core na komputerach Mac
description: Obsługiwane wersje macOS i zależności programu .NET Core umożliwiają tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach macOS.
author: mairaw
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 07/13/2019
ms.openlocfilehash: 4e0570beb0dd096d7d11cdcfb6a7ed20221c0386
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848956"
---
# <a name="prerequisites-for-net-core-on-macos"></a><span data-ttu-id="31596-103">Wymagania wstępne dotyczące platformy .NET Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="31596-103">Prerequisites for .NET Core on macOS</span></span>

<span data-ttu-id="31596-104">W tym artykule przedstawiono obsługiwane wersje programu macOS i zależności programu .NET Core, które są potrzebne do tworzenia, wdrażania i uruchamiania aplikacji platformy .NET Core na maszynach macOS.</span><span class="sxs-lookup"><span data-stu-id="31596-104">This article shows you the supported macOS versions and .NET Core dependencies that you need to develop, deploy, and run .NET Core applications on macOS machines.</span></span> <span data-ttu-id="31596-105">Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="31596-105">The supported OS versions and dependencies that follow apply to the three ways of developing .NET Core apps on a Mac: via the [command-line with your favorite editor](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/), and [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

## <a name="supported-macos-versions"></a><span data-ttu-id="31596-106">Obsługiwane wersje macOS</span><span class="sxs-lookup"><span data-stu-id="31596-106">Supported macOS versions</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31596-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="31596-107">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="31596-108">Program .NET Core 2. x jest obsługiwany przez następujące wersje programu macOS:</span><span class="sxs-lookup"><span data-stu-id="31596-108">.NET Core 2.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="31596-109">macOS 10,12 "Sierra" i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="31596-109">macOS 10.12 "Sierra" and later versions</span></span>

<span data-ttu-id="31596-110">Zobacz obsługiwane wersje systemu operacyjnego .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego .NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 2,1 i .NET Core 2,2 Obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.</span><span class="sxs-lookup"><span data-stu-id="31596-110">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) and [.NET Core 2.2 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) for the complete list of .NET Core 2.1 and .NET Core 2.2 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="31596-111">Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub w [programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="31596-111">For download links and more information, see [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2) or [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31596-112">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="31596-112">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="31596-113">Program .NET Core 1. x jest obsługiwany przez następujące wersje programu macOS:</span><span class="sxs-lookup"><span data-stu-id="31596-113">.NET Core 1.x is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="31596-114">macOS 10,12 "Sierra"</span><span class="sxs-lookup"><span data-stu-id="31596-114">macOS 10.12 "Sierra"</span></span>
* <span data-ttu-id="31596-115">macOS 10,11 "El Capitan"</span><span class="sxs-lookup"><span data-stu-id="31596-115">macOS 10.11 "El Capitan"</span></span>

<span data-ttu-id="31596-116">Zobacz obsługiwane wersje systemu operacyjnego .NET [core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) i [obsługiwane wersje systemu operacyjnego .NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 1,1 i .NET Core 1,0 obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.</span><span class="sxs-lookup"><span data-stu-id="31596-116">See [.NET Core 1.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) and [.NET Core 1.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) for the complete list of .NET Core 1.1 and .NET Core 1.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="31596-117">Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) lub w [programie .NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span><span class="sxs-lookup"><span data-stu-id="31596-117">For download links and more information, see [.NET Core 1.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.1) or [.NET Core 1.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/1.0).</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="31596-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="31596-118">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="31596-119">Program .NET Core 3,0 jest obsługiwany przez następujące wersje programu macOS:</span><span class="sxs-lookup"><span data-stu-id="31596-119">.NET Core 3.0 is supported on the following versions of macOS:</span></span>

* <span data-ttu-id="31596-120">macOS 10,13 "wysoka firma Sierra" i nowsze wersje</span><span class="sxs-lookup"><span data-stu-id="31596-120">macOS 10.13 "High Sierra" and later versions</span></span>

<span data-ttu-id="31596-121">Zobacz [obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 3,0, wersje systemu operacyjnego i linki do zasad cyklu życia.</span><span class="sxs-lookup"><span data-stu-id="31596-121">See [.NET Core 3.0 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) for the complete list of .NET Core 3.0 supported operating systems, distributions and versions, out of support OS versions, and lifecycle policy links.</span></span>

<span data-ttu-id="31596-122">Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="31596-122">For download links and more information, see [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>

---

## <a name="net-core-dependencies"></a><span data-ttu-id="31596-123">Zależności .NET Core</span><span class="sxs-lookup"><span data-stu-id="31596-123">.NET Core dependencies</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="31596-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="31596-124">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="31596-125">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="31596-125">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="31596-126">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z tematem [znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.1) dotyczące zainstalowanej wersji programu.</span><span class="sxs-lookup"><span data-stu-id="31596-126">If you have problems with the installation on macOS, consult the [Known issues](https://github.com/dotnet/core/tree/master/release-notes/2.1) topic for the version you have installed.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="31596-127">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="31596-127">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="31596-128">Program .NET Core 1. x wymaga OpenSSL podczas uruchamiania na macOS.</span><span class="sxs-lookup"><span data-stu-id="31596-128">.NET Core 1.x requires OpenSSL when running on macOS.</span></span> <span data-ttu-id="31596-129">Łatwym sposobem uzyskania OpenSSL jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS.</span><span class="sxs-lookup"><span data-stu-id="31596-129">An easy way to obtain OpenSSL is by using the [Homebrew ("brew")](https://brew.sh/) package manager for macOS.</span></span> <span data-ttu-id="31596-130">Po zainstalowaniu *rozwiązania brew*Zainstaluj OpenSSL, wykonując następujące polecenia w wierszu terminalu (polecenie):</span><span class="sxs-lookup"><span data-stu-id="31596-130">After installing *brew*, install OpenSSL by executing the following commands at a Terminal (command) prompt:</span></span>

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

<span data-ttu-id="31596-131">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="31596-131">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="31596-132">Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z tematem informacje o [znanych problemach](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znanych problemach](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) .</span><span class="sxs-lookup"><span data-stu-id="31596-132">If you have problems with the installation on macOS, consult the [1.0.0 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) and [1.0.1 Known Issues](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) topics.</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="31596-133">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="31596-133">.NET Core 3.0</span></span>](#tab/netcore30)

<span data-ttu-id="31596-134">Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="31596-134">Download and install the .NET Core SDK from the [.NET Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="31596-135">Jeśli masz problemy z instalacją na macOS, zapoznaj się z tematem [Informacje o wersji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) zainstalowanej wersji programu.</span><span class="sxs-lookup"><span data-stu-id="31596-135">If you have problems with the installation on macOS, consult the [Release notes](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) topic for the version you have installed.</span></span>

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a><span data-ttu-id="31596-136">Zwiększ maksymalny limit otwartych plików (wersje .NET Core przed zestaw .NET Core SDK 2.0.2)</span><span class="sxs-lookup"><span data-stu-id="31596-136">Increase the maximum open file limit (.NET Core versions before .NET Core SDK 2.0.2)</span></span>

<span data-ttu-id="31596-137">W starszych wersjach programu .NET Core (przed zestaw .NET Core SDK 2.0.2) domyślny limit otwierania plików na macOS może być niewystarczający dla niektórych obciążeń .NET Core, takich jak przywracanie projektów lub uruchamianie testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="31596-137">In older .NET Core versions (before .NET Core SDK 2.0.2), the default open file limit on macOS may not be sufficient for some .NET Core workloads, such as restoring projects or running unit tests.</span></span>

<span data-ttu-id="31596-138">Można zwiększyć ten limit, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="31596-138">You can increase this limit by following these steps:</span></span>

1. <span data-ttu-id="31596-139">Za pomocą edytora tekstów Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_i Zapisz plik z tą zawartością:</span><span class="sxs-lookup"><span data-stu-id="31596-139">Using a text editor, create a new file _/Library/LaunchDaemons/limit.maxfiles.plist_, and save the file with this content:</span></span>

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
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

2. <span data-ttu-id="31596-140">W oknie terminalu uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="31596-140">In a terminal window, run the following command:</span></span>

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. <span data-ttu-id="31596-141">Aby zastosować te ustawienia, uruchom ponownie komputer Mac.</span><span class="sxs-lookup"><span data-stu-id="31596-141">Reboot your Mac to apply these settings.</span></span>

## <a name="visual-studio-for-mac"></a><span data-ttu-id="31596-142">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="31596-142">Visual Studio for Mac</span></span>

<span data-ttu-id="31596-143">Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="31596-143">You can use any editor to develop .NET Core applications using the .NET Core SDK.</span></span> <span data-ttu-id="31596-144">Jeśli jednak chcesz opracowywać aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, możesz użyć [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span><span class="sxs-lookup"><span data-stu-id="31596-144">However, if you want to develop .NET Core applications on a Mac in an integrated development environment, you can use [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span>

<span data-ttu-id="31596-145">Programowanie na platformie .NET Core w systemie macOS z Visual Studio dla komputerów Mac wymaga:</span><span class="sxs-lookup"><span data-stu-id="31596-145">.NET Core development on macOS with Visual Studio for Mac requires:</span></span>

* <span data-ttu-id="31596-146">Obsługiwana wersja systemu operacyjnego macOS</span><span class="sxs-lookup"><span data-stu-id="31596-146">A supported version of the macOS operating system</span></span>
* <span data-ttu-id="31596-147">OpenSSL (tylko program .NET Core 1. x; program .NET Core 2. x używa usług zabezpieczeń dostępnych natywnie w macOS)</span><span class="sxs-lookup"><span data-stu-id="31596-147">OpenSSL (.NET Core 1.x only; .NET Core 2.x uses security services available natively in macOS)</span></span>
* <span data-ttu-id="31596-148">Zestaw .NET Core SDK dla komputerów Mac</span><span class="sxs-lookup"><span data-stu-id="31596-148">.NET Core SDK for Mac</span></span>
* [<span data-ttu-id="31596-149">Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="31596-149">Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
