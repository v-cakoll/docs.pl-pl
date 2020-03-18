---
title: Zależności sdk i runtime programu .NET Core — .NET Core
description: Szczegóły systemu operacyjnego i architektury procesora CPU wymagania wstępne do zainstalowania .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 12/04/2019
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca86b3c158bb38c1293cd4303dcf4c00ea9175b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157816"
---
# <a name="net-core-dependencies-and-requirements"></a>Zależności i wymagania programu .NET Core

W tym artykule opisano, które systemy operacyjne i architektura procesora są obsługiwane przez program .NET Core.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

Następujące wersje systemu Windows są obsługiwane z .NET Core 3.1:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.1, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

Następujące wersje systemu Windows są obsługiwane z .NET Core 3.0:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2012 R2+                       | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.0, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

Następujące wersje systemu Windows są obsługiwane z .NET Core 2.2:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Wersja 1803+                   | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.2, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Następujące wersje systemu Windows są obsługiwane z .NET Core 2.1:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 SP1+, 8.1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607+                  | x64, x86        |
| Windows Server                | 2008 R2 SP1+                   | x64, x86        |
| Nano Server                   | Wersja 1803+                  | x64,            |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.1, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2"></a>Windows 7 / Vista / 8.1 / Serwer 2008 R2

Dodatkowe zależności są wymagane w przypadku instalowania sdk .NET lub środowiska uruchomieniowego w następujących wersjach systemu Windows:

- Windows 7 z dodatkiem SP1
- Dodatek SP 2 dla systemu Windows Vista
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Zainstaluj następujące elementy:

- [Aktualizacja redystrybucyjna programu Microsoft Visual C++ 2015 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Powyższe wymagania są również wymagane, jeśli natkniesz się na jeden z następujących błędów:

> Nie można uruchomić programu, ponieważ na komputerze brakuje pliku *api-ms-win-crt-runtime-l1-1-0.dll.* Spróbuj ponownie zainstalować program, aby rozwiązać ten problem.
>
> \-lub -
>
> Znaleziono *hostfxr.dll* biblioteki, ale ładowanie go z *C:\\\<path_to_app>\\hostfxr.dll* nie powiodło się.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3.1](#tab/netcore31)

.NET Core 3.1 traktuje Linuksa jako jeden system operacyjny. Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.

.NET Core 3.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

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
| Linux Mennica                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 sp2+               | x64 |
| Alpejski Linux                   | 3.10+                 | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.1, zobacz [.NET Core 3.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Aby uzyskać więcej informacji na temat instalowania .NET Core 3.1 na ARM64 (jądro 4.14+), zobacz [Instalowanie .NET Core 3.0 w systemie Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Obsługa ARM64 wymaga jądra Systemu Linux 4.14 lub nowszego. Niektóre dystrybucje linuksa spełniają to wymaganie, podczas gdy inne nie. Na przykład Ubuntu 18.04 jest obsługiwany, ale Ubuntu 16.04 nie.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 traktuje Linuksa jako jeden system operacyjny. Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.

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
| Linux Mennica                     | 18+                   | x64 |
| openSUSE                       | 15+                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 sp2+               | x64 |
| Alpejski Linux                   | 3.8+                  | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3.0, zobacz [.NET Core 3.0 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3.0 na serwerze ARM64, zobacz [Instalowanie .NET Core 3.0 w systemie Linux ARM64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

.NET Core 2.2 traktuje Linuksa jako jeden system operacyjny. Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.

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
| Linux Mennica                     |  17, 18                 | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 sp2+                | x64 |
| Alpejski Linux                   |  3.8+                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.2, zobacz [.NET Core 2.2 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

.NET Core 2.1 traktuje Linuksa jako jeden system operacyjny. Istnieje pojedyncza kompilacja Systemu Linux (na architekturę chipów) dla obsługiwanych dystrybucji Linuksa.

.NET Core 2.1 jest obsługiwany w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| System operacyjny                             |  Wersja                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7+                     | x64 |
| Oracle Linux                   |  7+                     | x64 |
| Fedora                         |  29+                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16.04, 18.04, 19.04, 19.10    | x64, ARM32 |
| Linux Mennica                     |  17+                    | x64 |
| openSUSE                       |  15+                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 sp2+                | x64 |
| Alpejski Linux                   |  3.8+                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2.1, zobacz [.NET Core 2.1 Obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Zależności dystrybucji systemu Linux

Na podstawie dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.

> [!IMPORTANT]
> Dokładne wersje i nazwy mogą się nieznacznie różnić w wybranym przez Użytkownika dystrybucji Linuksa.

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

W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* należy również wykonać następującą zależność:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji Ubuntu zawiera wcześniejszą wersję libgdiplus. Możesz zainstalować najnowszą wersję libgdiplus, dodając repozytorium Mono do systemu. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS i Fedora

Dystrybucje CentOS wymagają zainstalowania następujących bibliotek:

- lttng-ust ( lttng ust )
- Libcurl
- openssl-libs
- krb5-libs
- libicu
- Zlib

Użytkownicy Fedory: Jeśli wersja OpenSSL >= 1.1, musisz zainstalować **compat-openssl10**.

W przypadku programu .NET Core 2.0 wymagane są również następujące zależności:

- libunwind ( libunwind )
- libuuid ( libuuid )

Aby uzyskać więcej informacji na temat zależności, zobacz [Niezależne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

W przypadku aplikacji .NET Core korzystających z zestawu *System.Drawing.Common* należy również wymagać następującej zależności:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji CentOS i Fedory zawiera wcześniejszą wersję libgdiplus. Możesz zainstalować najnowszą wersję libgdiplus, dodając repozytorium Mono do systemu. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

::: zone-end

::: zone pivot="os-macos"

Program .NET Core jest obsługiwany w następujących wersjach systemu macOS:

> [!NOTE]
> Symbol `+` reprezentuje wersję minimalną.

| Wersja podstawowa .NET | macOS                 | Architektury |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Wysokie Sierra (10.13+)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Wysokie Sierra (10.13+)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12+)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12+)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Począwszy od systemu macOS Catalina (wersja 10.15), całe oprogramowanie zbudowane po 1 czerwca 2019 r., które jest dystrybuowane z identyfikatorem dewelopera, musi zostać ponotowane powadnianiem notarialnie. To wymaganie dotyczy programu .NET Core, .NET Core SDK i oprogramowania utworzonego za pomocą programu .NET Core.

Instalatory .NET Core (zarówno w czasie wykonywania, jak i SDK) w wersjach 3.1, 3.0 i 2.1 zostały notarialnie notarialnie od lutego 18, 2020. Wcześniej wydane wersje nie są notarialnie. Jeśli uruchomisz aplikację nienotarialnie, zobaczysz błąd podobny do następującego obrazu:

![Alert notariacyjny macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

Aby uzyskać więcej informacji na temat wpływu wymuszanego notarializacji na program .NET Core (i aplikacje .NET Core), zobacz [Praca z notarialniem Catalina](macos-notarization-issues.md)w systemie macOS .

## <a name="libgdiplus"></a>libgdiplus ( libgdiplus )

Aplikacje .NET Core korzystające z zestawu *System.Drawing.Common* wymagają zainstalowania programu libgdiplus.

Łatwym sposobem uzyskania libgdiplus jest użycie menedżera pakietów [Homebrew ("brew")](https://brew.sh/) dla systemu macOS. Po zainstalowaniu *naparuzainstaluj*libgdiplus, wykonując następujące polecenia w wierszu Terminal (polecenie):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Następne kroki

- Aby tworzyć i uruchamiać aplikacje, zainstaluj [zestaw SDK .NET Core](sdk.md) (w tym czas wykonywania).
- Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [program .NET Core .](runtime.md)
