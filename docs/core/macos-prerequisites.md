---
title: Wymagania wstępne dotyczące platformy .NET Core dla komputerów Mac
description: Obsługiwane wersje macOS i zależności platformy .NET Core na tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach macOS.
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 09/27/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c33b1241-ab66-4583-9eba-52cf51146f5a
ms.workload:
- dotnetcore
ms.openlocfilehash: 4bad51e7d0d705ea730382edf80850bca15c5e7a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="prerequisites-for-net-core-on-macos"></a>Wymagania wstępne dotyczące .NET Core na macOS

W tym artykule przedstawiono macOS obsługiwane wersje i zależności platformy .NET Core, umożliwiające tworzenie, wdrażanie i uruchamianie aplikacji .NET Core na maszynach macOS. Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionego edytora](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Programu visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/).

## <a name="supported-macos-versions"></a>System macOS obsługiwane wersje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Oprogramowanie .NET core 2.x jest obsługiwana w następujących wersjach macOS:

* System macOS 10.12 "Sierra" i nowszymi wersjami

Zobacz [2.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) Pełna lista .NET Core 2.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Oprogramowanie .NET core 1.x jest obsługiwana w następujących wersjach macOS:

* System macOS 10.12 "Sierra"
* System macOS 10.11 "El Capitan"

Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) Pełna lista .NET Core 1.x obsługiwanych systemów operacyjnych, poza wersje obsługi systemu operacyjnego i łącza do zasad cyklu życia.

---

## <a name="net-core-dependencies"></a>Zależności .NET core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pobierz i zainstaluj .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core). Jeśli masz problemy z instalacją na macOS, należy skontaktować się [znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.0) tematu zainstalowaną wersję.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**.NET Core 1.x**

Oprogramowanie .NET core 1.x wymaga biblioteki OpenSSL, podczas uruchamiania na macOS. Jest łatwy sposób uzyskać biblioteki OpenSSL przy użyciu [Homebrew ("brew")](https://brew.sh/) Menedżer pakietów dla macOS. Po zainstalowaniu *brew*, zainstaluj biblioteki OpenSSL, wykonując następujące polecenia w wierszu terminali (polecenie):

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Pobierz i zainstaluj .NET Core SDK z [pobiera .NET](https://www.microsoft.com/net/download/core). Jeśli masz problemy z instalacją na macOS, należy skontaktować się [1.0.0 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) tematów.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Zwiększ limit maksymalnego Otwórz plik (wersje .NET Core przed .NET Core SDK pkt 2.0.2) 

W starszych wersjach platformy .NET Core (przed .NET Core SDK pkt 2.0.2) domyślny limit Otwórz plik na macOS nie może być wystarczające dla niektórych obciążeń .NET Core, takich jak przywracanie projektów lub przeprowadzanie testów jednostkowych.

Aby zwiększyć ten limit, należy wykonać następujące czynności:

1. Za pomocą edytora tekstu, Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_i Zapisz plik z tą zawartością:

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

2. W oknie terminalu uruchom następujące polecenie:

```console
echo 'ulimit -n 2048' | sudo tee -a /etc/profile
```

3. Ponowny rozruch komputera Mac, aby zastosować te ustawienia.

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora. Jednak jeśli chcesz wdrażać aplikacje .NET Core na komputerze Mac w zintegrowane środowisko programistyczne, można użyć [programu Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/). 

Tworzenie aplikacji platformy .NET core na macOS z programem Visual Studio for Mac wymaga:

* Obsługiwana wersja systemu operacyjnego macOS
* Biblioteki OpenSSL (.NET Core 1.x tylko; dostępna natywnie w macOS usług zabezpieczeń używa 2.x .NET Core)
* Oprogramowanie .NET core SDK dla komputerów Mac
* [Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)
