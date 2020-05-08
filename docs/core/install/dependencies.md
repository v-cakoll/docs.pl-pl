---
title: Zależności zestaw .NET Core SDK i środowiska uruchomieniowego — .NET Core
description: Szczegółowe informacje na temat wymagań wstępnych dotyczących architektury procesora i systemu operacyjnego w celu zainstalowania zestaw .NET Core SDK i środowiska uruchomieniowego w systemach Windows, Linux i macOS.
author: leecow
ms.author: leecow
ms.date: 04/30/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 280aa1431686ff99257580bb024a84b1e57f85c0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895490"
---
# <a name="net-core-dependencies-and-requirements"></a>Zależności i wymagania dotyczące platformy .NET Core

W tym artykule szczegółowo przedstawiono systemy operacyjne i architekturę procesora CPU obsługiwane przez platformę .NET Core.

## <a name="supported-operating-systems"></a>Obsługiwane systemy operacyjne

::: zone pivot="os-windows"

<!-- markdownlint-disable MD025 -->
<!-- markdownlint-disable MD024 -->

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

W przypadku programu .NET Core 3,1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

W przypadku programu .NET Core 3,0 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2012 R2 +                       | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

W przypadku programu .NET Core 2,2 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 Z DODATKIEM SP1 +                   | x64, x86        |
| Nano Server                   | Wersja 1803 +                   | x64, ARM32      |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

W przypadku programu .NET Core 2,1 obsługiwane są następujące wersje systemu Windows:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                            | Wersja                        | Architektury   |
| ----------------------------- | ------------------------------ | --------------- |
| Klient systemu Windows                | 7 Z DODATKIEM SP1 +, 8,1                    | x64, x86        |
| Klient systemu Windows 10             | Wersja 1607 +                  | x64, x86        |
| Windows Server                | 2008 R2 Z DODATKIEM SP1 +                   | x64, x86        |
| Nano Server                   | Wersja 1803 +                  | procesorów            |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

<!-- markdownlint-disable MD001 -->

### <a name="windows-7--vista--81--server-2008-r2--server-2012-r2"></a><a name="additional-deps"></a>Windows 7/Vista/8,1/Server 2008 R2/serwer 2012 R2

Jeśli instalujesz zestaw .NET SDK lub środowisko uruchomieniowe w następujących wersjach systemu Windows, wymagane są dodatkowe zależności:

- Windows 7 z dodatkiem SP1
- Windows Vista z dodatkiem SP 2
- Windows 8.1
- Windows Server 2008 R2
- Windows Server 2012 R2

Zainstaluj następujące elementy:

- [Microsoft Visual C++ 2015 redystrybucyjnej aktualizacji 3](https://www.microsoft.com/download/details.aspx?id=52685).
- [POPRAWKI KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot)

Powyższe wymagania są również wymagane w przypadku wystąpienia jednego z następujących błędów:

> Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-CRT-Runtime-L1-1 -0. dll* . Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.
>
> \-oraz
>
> Nie można uruchomić programu, ponieważ na komputerze brakuje *interfejsu API-ms-win-cor-timezone-L1-1 -0. dll* . Spróbuj zainstalować ponownie program, aby rozwiązać ten problem.
>
> \-oraz
>
> Znaleziono bibliotekę *hostfxr. dll* , ale ładowanie jej z *dysku C:\\\<path_to_app>\\hostfxr. dll* nie powiodło się.

::: zone-end

::: zone pivot="os-linux"

# <a name="net-core-31"></a>[.NET Core 3,1](#tab/netcore31)

Program .NET Core 3,1 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Platforma .NET Core 3,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                             | Wersja               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7 +                    | x64 |
| Oracle Linux                   | 7 +                    | x64 |
| Fedora                         | 30 +                   | x64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Mennic systemu Linux                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 Z DODATKIEM SP2 +               | x64 |
| Alpine Linux                   | 3.10 +                 | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,1, zobacz [.net core 3,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md).

Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,1 w systemie ARM64 (jądro 4.14 +), zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

> [!IMPORTANT]
> Obsługa ARM64 wymaga jądra systemu Linux 4,14 lub nowszego. Niektóre dystrybucje systemu Linux spełniają to wymaganie, a inne nie. Na przykład Ubuntu 18,04 jest obsługiwany, ale Ubuntu 16,04 nie jest.

# <a name="net-core-30"></a>[.NET Core 3.0](#tab/netcore30)

*Platforma .NET Core 3,0 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Program .NET Core 3,0 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Platforma .NET Core 3,0 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                             | Wersja               | Architektury    |
| ------------------------------ | --------------------- | ---------------- |
| Red Hat Enterprise Linux       | 6, 7, 8               | x64 |
| CentOS                         | 7 +                    | x64 |
| Oracle Linux                   | 7 +                    | x64 |
| Fedora                         | 29 +                   | x64 |
| Debian                         | 9 +                    | x64, ARM32, ARM64 |
| Ubuntu                         | 16.04 +                | x64, ARM32, ARM64 |
| Mennic systemu Linux                     | 18 +                   | x64 |
| openSUSE                       | 15 +                   | x64 |
| SUSE Enterprise Linux (SLES)   | 12 Z DODATKIEM SP2 +               | x64 |
| Alpine Linux                   | 3.8 +                  | x64, ARM64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 3,0, zobacz [.net core 3,0 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md).

Aby uzyskać więcej informacji na temat instalowania programu .NET Core 3,0 w systemie ARM64, zobacz [Instalowanie programu .net core 3,0 w systemie Linux arm64](https://gist.github.com/richlander/467813274cea8abc624553ee72b28213).

# <a name="net-core-22"></a>[.NET Core 2.2](#tab/netcore22)

*Platforma .NET Core 2,2 jest obecnie nieobsługiwana. Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).*

Program .NET Core 2,2 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Platforma .NET Core 2,2 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                             |  Wersja                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7                   | x64 |
| CentOS                         |  7                      | x64 |
| Oracle Linux                   |  7                      | x64 |
| Fedora                         |  29, 30                 | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 18,10    | x64, ARM32 |
| Mennic systemu Linux                     |  17, 18                 | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 Z DODATKIEM SP2 +                | x64 |
| Alpine Linux                   |  3.8 +                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,2, zobacz [.net core 2,2 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md).

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

Program .NET Core 2,1 traktuje system Linux jako pojedynczy systemu operacyjnego. Istnieje jedna kompilacja systemu Linux (dla architektury mikroukład) dla obsługiwanych dystrybucji systemu Linux.

Platforma .NET Core 2,1 jest obsługiwana w następujących dystrybucjach/wersjach systemu Linux:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| System operacyjny                             |  Wersja                |  Architektury   |
| ------------------------------ | ----------------------- | ---------------- |
| Red Hat Enterprise Linux       |  6, 7, 8                | x64 |
| CentOS                         |  7 +                     | x64 |
| Oracle Linux                   |  7 +                     | x64 |
| Fedora                         |  30 +                    | x64 |
| Debian                         |  9                      | x64, ARM32 |
| Ubuntu                         |  16,04, 18,04, 19,04, 19,10    | x64, ARM32 |
| Mennic systemu Linux                     |  17 +                    | x64 |
| openSUSE                       |  15 +                    | x64 |
| SUSE Enterprise Linux (SLES)   |  12 Z DODATKIEM SP2 +                | x64 |
| Alpine Linux                   |  3.8 +                   | x64 |

Aby uzyskać więcej informacji na temat obsługiwanych systemów operacyjnych, dystrybucji i zasad cyklu życia programu .NET Core 2,1, zobacz [.net core 2,1 obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md).

---

## <a name="linux-distribution-dependencies"></a>Zależności dystrybucji systemu Linux

W zależności od dystrybucji systemu Linux może być konieczne zainstalowanie dodatkowych zależności.

> [!IMPORTANT]
> Dokładne wersje i nazwy mogą się nieco różnić w zależności od wybranej dystrybucji systemu Linux.

### <a name="ubuntu"></a>Ubuntu

W przypadku dystrybucji Ubuntu wymagane jest zainstalowanie następujących bibliotek:

- liblttng-ust0
- libcurl3 (dla 14. x i 16. x)
- libcurl4 (dla 18. x)
- libssl 1.0.0
- libkrb5-3
- zlib1g
- libicu52 (dla 14. x)
- libicu55 (dla 16. x)
- libicu57 (dla 17. x)
- libicu60 (dla 18. x)

W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji programu Ubuntu obejmuje wcześniejszą wersję libgdiplus. Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

### <a name="centos-and-fedora"></a>CentOS i Fedora

Dystrybucje CentOS wymagają zainstalowanych następujących bibliotek:

- LTTng — zespół sklepu uniwersalnego
- libcurl
- OpenSSL — libs
- krb5 — libs
- libicu
- zlib

Fedora użytkownicy: Jeśli OpenSSL wersja >= 1,1, należy zainstalować polecenie **COMPAT-openssl10**.

W przypadku platformy .NET Core 2,0 wymagane są również następujące zależności:

- libunwind
- libuuid

Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:

- libgdiplus (wersja 6.0.1 lub nowsza)

> [!WARNING]
> Większość wersji CentOS i Fedora obejmuje wcześniejszą wersję libgdiplus. Aby zainstalować najnowszą wersję programu libgdiplus, można dodać do systemu repozytorium mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

### <a name="alpine"></a>Alp

Dystrybucje Alpine wymagają zainstalowania następujących bibliotek:

- ICU-libs (nie jest to zbędne, jeśli Globalizacja jest wyłączona)
- krb5 — libs
- libcurl
- libintl
- libssl 1.1 (dla Alpine 3,9 lub nowszego) lub libssl 1.0 (dla starszych)
- libstdc + +
- LTTng — zespół sklepu uniwersalnego
- numactl (opcjonalne, przydatne tylko w przypadku urządzeń z włączoną architekturą NUMA)
- zlib

W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , wymagana jest również następująca zależność:

- libgdiplus (jest dostępny tylko w repozytorium brzeg/testowanie)

::: zone-end

::: zone pivot="os-macos"

Platforma .NET Core jest obsługiwana w następujących wersjach macOS:

> [!NOTE]
> `+` Symbol reprezentuje wersję minimalną.

| Wersja platformy .NET Core | macOS                 | Architektury |     |
| ----------------- | --------------------- | --------------| --- |
| 3.1               | Wysoka firma Sierra (10.13 +)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.1/3.1-supported-os.md) |
| 3.0               | Wysoka firma Sierra (10.13 +)  | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md) |
| 2.2               | Sierra (10.12 +)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md) |
| 2.1               | Sierra (10.12 +)       | x64 | [Więcej informacji](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) |

Począwszy od programu macOS Catalina (wersja 10,15), całe oprogramowanie skompilowane po 1 czerwca 2019, które jest dystrybuowane z IDENTYFIKATORem dewelopera, musi być notarialne. To wymaganie dotyczy środowiska uruchomieniowego .NET Core, zestaw .NET Core SDK i oprogramowania utworzonego za pomocą platformy .NET Core.

Instalatory dla programu .NET Core (zarówno środowisko uruchomieniowe, jak i zestaw SDK) w wersji 3,1, 3,0 i 2,1 zostały zgłoszone od 18 lutego 2020. Wcześniejsze wersje nie zostały ujawnione. Jeśli uruchomisz zanotarialną aplikację, zobaczysz komunikat o błędzie podobny do następującego:

![Alert notarization macOS Catalina](media/dependencies/macos-notarized-pkg-warning.png)

Aby uzyskać więcej informacji na temat sposobu, w jaki wymuszone — notarization wpływa na platformę .NET Core (i aplikacje platformy .NET Core), zobacz [Praca z MacOS Catalina notarization](macos-notarization-issues.md).

## <a name="libgdiplus"></a>libgdiplus

Aplikacje .NET Core używające zestawu *System. Drawing. Common* wymagają zainstalowania libgdiplus.

Łatwym sposobem uzyskania libgdiplus jest użycie Menedżera pakietów [oprogramowania homebrew ("rozwiązania brew")](https://brew.sh/) dla macOS. Po zainstalowaniu *rozwiązania brew*Zainstaluj libgdiplus, wykonując następujące polecenia w wierszu terminalu (polecenie):

```console
brew update
brew install mono-libgdiplus
```

::: zone-end

## <a name="next-steps"></a>Następne kroki

- Aby opracowywać i uruchamiać aplikacje, zainstaluj [zestaw .NET Core SDK](sdk.md) (w tym środowisko uruchomieniowe).
- Aby uruchamiać aplikacje utworzone przez inne osoby, zainstaluj [środowisko uruchomieniowe programu .NET Core](runtime.md).
