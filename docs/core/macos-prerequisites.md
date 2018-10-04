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
# <a name="prerequisites-for-net-core-on-macos"></a>Wymagania wstępne dla platformy .NET Core w systemie macOS

W tym artykule przedstawiono macOS obsługiwane wersje i zależności platformy .NET Core, umożliwiające tworzenie, wdrażanie i uruchamianie aplikacji platformy .NET Core na maszynach z systemem macOS. Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby związanych z tworzeniem aplikacji .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia za pomocą ulubionego edytora](tutorials/using-with-xplat-cli.md), [programu Visual Studio Code](https://code.visualstudio.com/)i [Programu visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>Obsługiwane w systemie macOS w wersji

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

.NET core 2.x jest obsługiwane w następujących wersji systemu MacOS:

* System macOS 10.12 "Sierra" i nowsze wersje

Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 2.x](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) kompletną listę platformy .NET Core 2.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

.NET core 1.x jest obsługiwane w następujących wersji systemu MacOS:

* System macOS 10.12 "Sierra"
* System macOS 10.11 "El Capitan"

Zobacz [obsługiwanych wersjach systemu operacyjnego programu .NET Core 1.x](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) kompletną listę platformy .NET Core 1.x obsługiwane systemy operacyjne, poza pomocy technicznej systemu operacyjnego, wersji i łączy zasady cyklu życia.

---

## <a name="net-core-dependencies"></a>Zależności platformy .NET core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core). Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [znane problemy dotyczące](https://github.com/dotnet/core/tree/master/release-notes/2.1) temacie zainstalowaną wersję.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.x**

.NET core 1.x wymaga biblioteki OpenSSL, podczas uruchamiania w systemie macOS. Łatwym sposobem uzyskiwania OpenSSL polega na użyciu [Homebrew ("brew")](https://brew.sh/) Menedżer pakietów dla systemu macOS. Po zainstalowaniu *brew*, zainstalować protokół OpenSSL, wykonując następujące polecenia w wierszu terminalu (polecenie):

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Pobierz i zainstaluj zestaw .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core). Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 — znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematów.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Zwiększ limit maksymalny otwartego pliku (wersje platformy .NET Core przed zestawu .NET Core SDK pkt 2.0.2) 

W starszych wersjach platformy .NET Core (przed zestawu .NET Core SDK pkt 2.0.2) domyślny limit Otwórz plik w systemie macOS może nie być wystarczające dla niektórych obciążeń platformy .NET Core, takich jak przywracanie projektów lub Uruchamianie testów jednostkowych.

Aby zwiększyć ten limit, należy wykonać następujące czynności:

1. Za pomocą edytora tekstu Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_, a następnie zapisz plik z tą zawartością:

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

2. W oknie terminala uruchom następujące polecenie:

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. Ponowny rozruch komputera Mac, aby zastosować te ustawienia.

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora. Jednakże, jeśli chcesz tworzyć aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, można użyć [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/). 

Programowanie aplikacji platformy .NET core w systemie macOS przy użyciu programu Visual Studio for Mac wymaga:

* Obsługiwana wersja systemu operacyjnego z systemem macOS
* Biblioteki OpenSSL (.NET Core 1.x tylko; .NET Core 2.x używa zabezpieczeń usług dostępnych natywnie w systemie macOS)
* .NET core SDK dla komputerów Mac
* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/visual-studio-mac/)
