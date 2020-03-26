---
title: Zależności core sdk i środowiska uruchomieniowego platformy .NET — .NET Core
description: Szczegółowe informacje o wymaganiach wstępnych dotyczących systemu operacyjnego i architektury procesora, aby zainstalować pakiet .NET Core SDK i środowisko wykonawcze w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 023b8fdf029dd6b17fe2186296d87dd7507c60b5
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546565"
---
# <a name="net-core-dependencies-and-requirements"></a>Zależności i wymagania podstawowe platformy .NET

W tym artykule opisano, które systemy operacyjne i architektura procesora są obsługiwane przez program .NET Core.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Rdzeń 3.1](#tab/netcore31)

Z programem .NET Core 3.1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Program .NET Core 3.0 jest obecnie niew pomocy technicznej. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Z programem .NET Core 3.0 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.0 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2.2 jest obecnie poza wsparciem. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Z programem .NET Core 2.2 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Wersja 1803+                   | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.2 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Z programem .NET Core 2.1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64,            |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Serwer 2008 R2

Dodatkowe zależności są wymagane, jeśli instalujesz pakiet .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows:

- Windows 7 z dodatkiem SP1
- Dodatek SP 2 dla systemu Windows Vista
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Zainstaluj następujące instalacje:

- [Microsoft Visual C++ 2015 Redystrybucjowa aktualizacja 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [aktualizacja kb2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Powyższe wymagania są również wymagane, jeśli natkniesz się na jeden z następujących błędów:

> Program nie może się uruchomić, ponieważ na komputerze brakuje *pliku api-ms-win-crt-runtime-l1-1-0.dll.* Spróbuj ponownie zainstalować program, aby rozwiązać ten problem.
>
> \-lub -
>
> Znaleziono *hostfxr.dll* biblioteki, ale ładowanie go z *języka C:\\\<path_to_app>\\hostfxr.dll* nie powiodło się.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Rdzeń 3.1](#tab/netcore31)

.NET Core 3.1 traktuje Linuksa jako jeden system operacyjny. Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.

.NET Core 3.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                             | Wersja               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 30+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 sp2+               | x64 |
| Alpejski Linux                   | 3.10+                 | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Aby uzyskać więcej informacji o tym, jak zainstalować .NET Core 3.1 na ARM64 (jądro 4.14+), zobacz [Instalowanie .NET Core 3.0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Obsługa ARM64 wymaga jądra Linuksa 4.14 lub nowszego. Niektóre dystrybucje Linuksa spełniają to wymaganie, podczas gdy inne nie. Na przykład Ubuntu 18.04 jest obsługiwany, ale Ubuntu 16.04 nie.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Program .NET Core 3.0 jest obecnie niew pomocy technicznej. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 3.0 traktuje Linuksa jako jeden system operacyjny. Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.

.NET Core 3.0 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                             | Wersja               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7+                    | x64 |
| Oracle Linux                   | 7+                    | x64 |
| Fedora                         | 29+                   | x64 |
| Debian                         | 9+                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04+                | x64, ARM32, ARM64 |
| Linux Mint                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 sp2+               | x64 |
| Alpejski Linux                   | 3,8+                  | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 3.0 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Aby uzyskać więcej informacji o tym, jak zainstalować .NET Core 3.0 na ARM64, zobacz [Instalowanie .NET Core 3.0 na Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*.NET Core 2.2 jest obecnie poza wsparciem. Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

.NET Core 2.2 traktuje Linuksa jako jeden system operacyjny. Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.

.NET Core 2.2 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                             |  Wersja                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 18.10    | x64, ARM32 |
| Linux Mint                     |  17, 18                 | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 sp2+                | x64 |
| Alpejski Linux                   |  3,8+                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.2 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 traktuje Linuksa jako jeden system operacyjny. Istnieje jedna kompilacja Linuksa (na architekturę chipa) dla obsługiwanych dystrybucji Linuksa.

.NET Core 2.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                             |  Wersja                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  30+                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux Mint                     |  17+                    | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 sp2+                | x64 |
| Alpejski Linux                   |  3,8+                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych przez firmę .NET Core 2.1 systemów operacyjnych, dystrybucji i zasad cyklu życia, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Zależności dystrybucji systemu Linux

Na podstawie dystrybucji linuksa może być konieczne zainstalowanie dodatkowych zależności.

> [!IMPORTANT]
> Dokładne wersje i nazwy mogą się nieznacznie różnić w wybranej dystrybucji Linuksa.

### <a name="ubuntu"></a>Ubuntu

Dystrybucje Ubuntu wymagają zainstalowania następujących bibliotek:

- liblttng-ust0
- libcurl3 (dla 14.x i 16.x)
- libcurl4 (dla 18.x)
- libssl1.0.0
- libkrb5-3
- zlib1g
- libicu52 (dla 14.x)
- libicu55 (dla 16.x)
- libicu57 (dla 17.x)
- libicu60 (dla 18.x)

W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* potrzebne są również następujące zależności:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji Ubuntu zawiera wcześniejszą wersję libgdiplus. Najnowszą wersję libgdiplus można zainstalować, dodając do systemu repozytorium Mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS i Fedora

Dystrybucje centos wymagają następujących bibliotek zainstalowanych:

- lttng-ust
- Libcurl
- openssl-libs
- krb5-libs
- libicu
- Zlib

Użytkownicy Fedory: Jeśli wersja OpenSSL >= 1.1, musisz zainstalować **compat-openssl10**.

W przypadku platformy .NET Core 2.0 wymagane są również następujące zależności:

- libunwind
- libuuid

Aby uzyskać więcej informacji na temat zależności, zobacz [Samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* potrzebne są również następujące zależności:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji CentOS i Fedory zawiera wcześniejszą wersję libgdiplus. Najnowszą wersję libgdiplus można zainstalować, dodając do systemu repozytorium Mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

Program .NET Core jest obsługiwany w następujących wersjach systemu macOS:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| Wersja podstawowa .NET | macOS                 | Architektury |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Wysoka Sierra (10.13+)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Wysoka Sierra (10.13+)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12+)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Począwszy od systemu macOS Catalina (wersja 10.15), wszystkie programy utworzone po 1 czerwca 2019 r., które są dystrybuowane z identyfikatorem dewelopera, muszą zostać poś poś poś poś pośowiane notapozycją. To wymaganie dotyczy środowiska uruchomieniowego .NET Core, .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.

Instalatory programu .NET Core (zarówno środowiska uruchomieniowego, jak i SDK) w wersji 3.1, 3.0 i 2.1 zostały poś pośpomniejsione notapozycją od 18 lutego 2020 r. Wcześniej wydane wersje nie są pośa poś pośliczone notapozytem. Jeśli uruchomisz aplikację nieobjętą notawią, zobaczysz błąd podobny do następującego obrazu:

![alert notagizowania macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

Aby uzyskać więcej informacji o tym, jak wymuszona notapozycja wpływa na program .NET Core (i aplikacje .NET Core), zobacz [Praca z systemem macOS Catalina Notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Aplikacje .NET Core korzystające z *zestawu System.Drawing.Common* wymagają zainstalowania libgdiplus.

Łatwym sposobem uzyskania libgdiplus jest użycie menedżera pakietów [Homebrew ("brew")](https://brew.sh/) dla systemu macOS. Po *zainstalowaniu naparu*zainstaluj libgdiplus, wykonując następujące polecenia w wierszu polecenia Terminal (polecenie):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Następne kroki

- Aby tworzyć i uruchamiać aplikacje, zainstaluj [zestaw SDK .NET Core](sdk.md) (w tym środowisko wykonawcze).
- Aby uruchomić aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe .NET Core](runtime.md).
