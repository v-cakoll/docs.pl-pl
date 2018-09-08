---
title: Wymagania wstępne dla platformy .NET Core w Windows
description: Dowiedz się, jakie zależności dotyczące usługi Windows komputera na opracowywanie i uruchamianie aplikacji .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 08/31/2018
ms.openlocfilehash: 477d303b50495070ba3a3540188deb274dd9f510
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44179497"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Wymagania wstępne dla platformy .NET Core w Windows

W tym artykule przedstawiono zależności niezbędne do tworzenia aplikacji platformy .NET Core w Windows. Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na Windows:

* [Wiersz polecenia](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>.NET core, obsługiwane wersje serwera Windows

.NET core jest obsługiwana w następujących wersjach:

* Windows 7 z dodatkiem SP1
* Windows 8.1
* Rocznicowa aktualizacja (wersja 1607) dla systemu Windows 10 lub nowszy
* Windows Server 2008 R2 z dodatkiem SP1 (pełny serwer lub Server Core)
* Windows Server 2012 z dodatkiem SP1 (pełny serwer lub Server Core)
* Windows Server 2012 R2 (pełny serwer lub Server Core)
* Windows Server 2016 lub nowszy (pełny serwer, Server Core lub Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core, obsługiwane systemy operacyjne

Następujące artykuły mają pełną listę systemów operacyjnych .NET Core, obsługiwane poszczególnych wersji:

* [.NET core 2.1 — obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET core 2.0 — obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [.NET core 1.x — wersje obsługiwanych systemów operacyjnych](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a>Zależności platformy .NET core

.NET core 1.1 i wcześniejszych wersji wymagają pakietu redystrybucyjnego Visual C++, podczas uruchamiania na wersje Windows wcześniejsze niż Windows 10 i Windows Server 2016. Ta zależność jest automatycznie instalowany przez Instalatora programu .NET Core.

[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:

* Instalowanie platformy .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).
* Wdrażanie aplikacji .NET Core w niezależna.
* Kompilowanie produktu ze źródła.
* Instalowanie platformy .NET Core za pomocą *zip* pliku. Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.

> [!NOTE]
> **Dla Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersji:**
>
> Upewnij się, że instalacja Windows jest aktualny i zawiera [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), którą można zainstalować za pośrednictwem usługi Windows Update. Jeśli nie masz zainstalowano tę aktualizację, zobaczysz następujący błąd podczas uruchamiania aplikacji .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 lub Windows Server 2008 R2:**
>
> Oprócz KB2999226, upewnij się, masz także [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane. Jeśli nie zainstalowano tę aktualizację, zobaczysz błąd podobny do poniższego, podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-with-visual-studio-2017"></a>Wymagania wstępne dotyczące programu Visual Studio 2017

Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora. [Program Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko programistyczne dla aplikacji .NET Core w Windows.

Możesz dowiedzieć się więcej o zmianach wprowadzonych w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

Do tworzenia aplikacji platformy .NET Core 2.1 w programie Visual Studio 2017:

 1. [Pobierz i zainstaluj program Visual Studio 2017, wersja 15.7.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-15-8-workloads.jpg)

Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, domyślnie i .NET Core 2.0 SDK korzysta z programu Visual Studio 2017 w wersji 15.7 programu Visual Studio 2017 15.8 użyto zestawu SDK 2.1.

 2. Jeśli używasz programu Visual Studio 2017 w wersji 15.7, zainstaluj [zestawu SDK programu .NET Core 2.1](https://www.microsoft.com/net/download/core) lub uaktualnienia do programu Visual Studio 2017 15.8.

 3. Przekieruj istniejących lub nowych projektów .NET Core do platformy .NET Core 2.1 przy użyciu następujących instrukcji:
    * Na **projektu** menu, wybierz **właściwości**.
    * W **platformę docelową** menu wyboru, ustaw wartość **platformy .NET Core 2.1**.

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" Target framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Gdy program Visual Studio skonfigurowane przy użyciu zestawu SDK programu .NET Core 2.1, należy wykonać następujące czynności:

* Otwórz, tworzenia i uruchamiania istniejących projektów .NET Core 1.x i 2.x.
* Przekieruj platformy .NET Core 1.x i 2.0 projektów .NET Core 2.1, skompilować i uruchomić.
* Utwórz nowe projekty platformy .NET Core 2.1.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

Tworzenie aplikacji .NET Core 2.0, w programie Visual Studio 2017:

 1. [Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowana, program Visual Studio 2017 korzysta z platformy .NET Core 1.x domyślnie. Zainstaluj zestaw .NET Core 2.0 SDK można pobrać zestaw .NET Core 2.0 pomocy technicznej w programie Visual Studio 2017.

 2. Zainstaluj [.NET Core 2.0 SDK](https://www.microsoft.com/net/download/dotnet-core/2.0).
 3. Przekieruj istniejącej lub nowej platformy .NET Core 1.x projektów .NET Core 2.0 przy użyciu następujących instrukcji:
    * Na **projektu** menu, wybierz **właściwości**.
    * W **platformę docelową** menu wyboru, ustaw wartość **.NET Core 2.0**.

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" Target framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Po zainstalowaniu zestawu .NET Core 2.0 SDK programu Visual Studio 2017 domyślnie używa .NET Core SDK 2.0 i obsługuje następujące akcje:

* Otwórz, tworzenie i uruchamianie istniejących projektów programu .NET Core 1.x.
* Przekieruj projektów programu .NET Core 1.x do platformy .NET Core 2.0, kompilacja i uruchom.
* Utwórz nowe projekty .NET Core 2.0.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Tworzenie aplikacji .NET Core 1.x, w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z **"Programowanie dla wielu platform .NET Core"** obciążenia (w **inne zestawy narzędzi**sekcji) wybranego.

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x rozwoju, ale nie jest zalecane w następujących sytuacjach:
  > * Zestaw narzędzi .NET Core jest w wersji preview, która nie jest obsługiwana.
  > * Projekty są oparte na pliku project.json, które jest przestarzałe.
>
> Aby uzyskać więcej informacji na temat zmiany formatu projektu, zobacz [ogólny przegląd zmian](./tools/cli-msbuild-architecture.md).
---

<a name="vs-mapping"></a>

> [!TIP]
> Aby sprawdzić używanej wersji programu Visual Studio 2017:
>
> * Na **pomocy** menu, wybierz **Microsoft Visual Studio**.
> * W **Microsoft Visual Studio** okno dialogowe, sprawdź numer wersji.
>   * W przypadku aplikacji .NET Core 2.2 w wersji zapoznawczej 1, Visual Studio 2017 w wersji 15.9 (obecnie w wersji zapoznawczej) lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 2.1 programu Visual Studio 2017 w wersji 15.7 lub nowszej.
>   * W przypadku aplikacji .NET Core 2.0, programu Visual Studio 2017 w wersji 15.3 lub nowszej.
>   * W przypadku aplikacji .NET Core 1.x programu Visual Studio 2017 w wersji 15,0 lub nowszej.
