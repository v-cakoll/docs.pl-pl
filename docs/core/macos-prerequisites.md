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
# <a name="prerequisites-for-net-core-on-macos"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie macOS

W tym artykule przedstawiono obsługiwane wersje programu macOS i zależności programu .NET Core, które są potrzebne do tworzenia, wdrażania i uruchamiania aplikacji platformy .NET Core na maszynach macOS. Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core na komputerze Mac: za pośrednictwem [wiersza polecenia z ulubionym edytorem](tutorials/using-with-xplat-cli.md), [Visual Studio Code](https://code.visualstudio.com/)i [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

## <a name="supported-macos-versions"></a>Obsługiwane wersje macOS

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Program .NET Core 2. x jest obsługiwany przez następujące wersje programu macOS:

* macOS 10,12 "Sierra" i nowsze wersje

Zobacz obsługiwane wersje systemu operacyjnego .NET [core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) i [obsługiwane wersje systemu operacyjnego .NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 2,1 i .NET Core 2,2 Obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.

Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2) lub w [programie .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Program .NET Core 1. x jest obsługiwany przez następujące wersje programu macOS:

* macOS 10,12 "Sierra"
* macOS 10,11 "El Capitan"

Zobacz obsługiwane wersje systemu operacyjnego .NET [core 1,1](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md) i [obsługiwane wersje systemu operacyjnego .NET Core 1,0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) , aby zapoznać się z pełną listą systemów operacyjnych .NET Core 1,1 i .NET Core 1,0 obsługiwane systemy operacyjne, dystrybucje i wersje, nieobsługiwane wersje systemu operacyjnego i zasady cyklu życia linki.

Aby uzyskać linki do pobrania i więcej informacji, zobacz pliki do pobrania w [programie .net core 1,1](https://dotnet.microsoft.com/download/dotnet-core/1.1) lub w [programie .NET Core 1,0](https://dotnet.microsoft.com/download/dotnet-core/1.0).

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Program .NET Core 3,0 jest obsługiwany przez następujące wersje programu macOS:

* macOS 10,13 "wysoka firma Sierra" i nowsze wersje

Zobacz [obsługiwane wersje systemu operacyjnego .net core 3,0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) , aby uzyskać pełną listę obsługiwanych systemów operacyjnych, dystrybucje i wersje programu .net Core 3,0, wersje systemu operacyjnego i linki do zasad cyklu życia.

Aby uzyskać linki do pobrania i więcej informacji, zobacz temat [pobieranie z programu .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0).

---

## <a name="net-core-dependencies"></a>Zależności .NET Core

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) . Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z tematem [znane problemy](https://github.com/dotnet/core/tree/master/release-notes/2.1) dotyczące zainstalowanej wersji programu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Program .NET Core 1. x wymaga OpenSSL podczas uruchamiania na macOS. Łatwym sposobem uzyskania OpenSSL jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS. Po zainstalowaniu *rozwiązania brew*Zainstaluj OpenSSL, wykonując następujące polecenia w wierszu terminalu (polecenie):

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) . Jeśli masz problemy z instalacją w systemie macOS, zapoznaj się z tematem informacje o [znanych problemach](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md) i [1.0.1 znanych problemach](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md) .

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Pobierz i Zainstaluj zestaw .NET Core SDK ze strony [plików do pobrania platformy .NET](https://dotnet.microsoft.com/download) . Jeśli masz problemy z instalacją na macOS, zapoznaj się z tematem [Informacje o wersji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) zainstalowanej wersji programu.

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>Zwiększ maksymalny limit otwartych plików (wersje .NET Core przed zestaw .NET Core SDK 2.0.2)

W starszych wersjach programu .NET Core (przed zestaw .NET Core SDK 2.0.2) domyślny limit otwierania plików na macOS może być niewystarczający dla niektórych obciążeń .NET Core, takich jak przywracanie projektów lub uruchamianie testów jednostkowych.

Można zwiększyć ten limit, wykonując następujące czynności:

1. Za pomocą edytora tekstów Utwórz nowy plik _/Library/LaunchDaemons/limit.maxfiles.plist_i Zapisz plik z tą zawartością:

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

2. W oknie terminalu uruchom następujące polecenie:

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Aby zastosować te ustawienia, uruchom ponownie komputer Mac.

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK. Jeśli jednak chcesz opracowywać aplikacje .NET Core na komputerze Mac w zintegrowanym środowisku programistycznym, możesz użyć [Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).

Programowanie na platformie .NET Core w systemie macOS z Visual Studio dla komputerów Mac wymaga:

* Obsługiwana wersja systemu operacyjnego macOS
* OpenSSL (tylko program .NET Core 1. x; program .NET Core 2. x używa usług zabezpieczeń dostępnych natywnie w macOS)
* Zestaw .NET Core SDK dla komputerów Mac
* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
