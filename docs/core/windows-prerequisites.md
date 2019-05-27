---
title: Wymagania wstępne dla platformy .NET Core w Windows
description: Dowiedz się, jakie zależności dotyczące usługi Windows komputera na opracowywanie i uruchamianie aplikacji .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 423a333edf5b2946a28855352adf2915642b1eae
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051970"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Wymagania wstępne dla platformy .NET Core w Windows

W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji .NET Core na Windows. Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core na Windows:

* [Wiersz polecenia](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Ponadto, jeśli tworzysz Windows przy użyciu programu Visual Studio 2017, [wstępnie wymaganych składników w programie Visual Studio 2017](#prerequisites-with-visual-studio-2017) sekcji znajduje się w bardziej szczegółowo wersje minimalną obsługę programowania .NET Core.

## <a name="net-core-supported-windows-versions"></a>.NET core, obsługiwane wersje serwera Windows

.NET core jest obsługiwana w następujących wersjach:

* Windows 7 SP1
* Windows 8.1
* Rocznicowa aktualizacja (wersja 1607) dla systemu Windows 10 lub nowszy
* Windows Server 2008 R2 z dodatkiem SP1 (pełny serwer lub Server Core)
* Windows Server 2012 z dodatkiem SP1 (pełny serwer lub Server Core)
* Windows Server 2012 R2 (pełny serwer lub Server Core)
* Windows Server 2016 lub nowszy (pełny serwer, Server Core lub Nano Server)

## <a name="net-core-supported-operating-systems"></a>.NET core, obsługiwane systemy operacyjne

Następujące artykuły mają pełną listę systemów operacyjnych .NET Core, obsługiwane poszczególnych wersji:

* [.NET core 3.0 (wersja zapoznawcza)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Łącza pobierania oraz więcej informacji, zobacz [pobiera .NET](https://dotnet.microsoft.com/download) Aby pobrać najnowszą wersję lub [.NET pobiera archiwum](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.

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
> Upewnij się, że instalacja Windows jest aktualny i zawiera [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), którą można zainstalować za pośrednictwem usługi Windows Update. Jeśli nie masz zainstalowano tę aktualizację, zobaczysz następujący błąd podczas uruchamiania aplikacji .NET Core: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Windows 7 lub Windows Server 2008 R2:**
>
> Oprócz KB2999226, upewnij się, masz także [KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane. Jeśli nie zainstalowano tę aktualizację, zobaczysz błąd podobny do poniższego, podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>Wymagania wstępne dla platformy .NET Core 3.0 w wersji zapoznawczej 3

.NET core 3.0 w wersji zapoznawczej 3 ma takie same wymagania wstępne w innych wersjach programu .NET Core. Jeśli chcesz użyć programu Visual Studio do tworzenia platformy .NET Core 3.0 projektów, należy użyć [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Visual Studio 2019 r mogą być zainstalowane side-by-side z innymi wersjami programu Visual Studio bez powodowania konfliktów.

## <a name="prerequisites-with-visual-studio-2017"></a>Wymagania wstępne dotyczące programu Visual Studio 2017
    
Tworzenie aplikacji .NET Core przy użyciu zestawu .NET Core SDK, można użyć dowolnego edytora. Program Visual Studio 2017 udostępnia zintegrowane środowisko programistyczne dla aplikacji .NET Core w Windows.

Możesz dowiedzieć się więcej o zmianach wprowadzonych w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Aby opracować aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu .NET Core 2.2 SDK:

 1. [Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z **programowanie dla wielu platform .NET Core** obciążenie (w **inne zestawy narzędzi** sekcji) wybranego.

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po **programowanie dla wielu platform .NET Core** zestawu narzędzi jest zainstalowana, program Visual Studio instaluje zwykle poprzedniej wersji programu .NET Core SDK.
Na przykład program Visual Studio 2017 15.9 używa zestawu SDK programu .NET Core 2.1 domyślnie po zainstalowaniu obciążenia.

Aby zaktualizować program Visual Studio, aby użyć zestawu .NET Core 2.2 SDK:

 1. Zainstaluj [.NET Core SDK 2,2](https://dotnet.microsoft.com/download).

 1. Jeśli chcesz, aby projekt do najnowsze środowisko uruchomieniowe platformy .NET Core, należy przekierować istniejących lub nowych projektów .NET Core do wersji 2.2 podstawowych platformy .NET przy użyciu następujących instrukcji:

    * Na **projektu** menu, wybierz **właściwości**.
    * W **platformę docelową** menu wyboru, ustaw wartość **platformy .NET Core 2.2**.

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.2" target framework wybranego elementu](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Gdy program Visual Studio skonfigurowane przy użyciu zestawu .NET Core 2.2 SDK, należy wykonać następujące czynności:

* Otwórz, tworzenia i uruchamiania istniejących projektów .NET Core 1.x i 2.x.
* Przekierowanie wersji 1.x i 2.x projektów .NET Core do platformy .NET Core 2.2, kompilacja i uruchom.
* Utwórz nowe projekty platformy .NET Core 2.2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Tworzenie aplikacji .NET Core 1.x, w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z **"Programowanie dla wielu platform .NET Core"** obciążenia (w **inne zestawy narzędzi**sekcji) wybranego.

![Zrzut ekranu programu Visual Studio 2017 instalacji z wybranym pakietem roboczym "Programowanie dla wielu platform .NET Core"](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x rozwoju, ale nie jest zalecane w następujących sytuacjach:
  > * Zestaw narzędzi .NET Core jest w wersji preview, która nie jest obsługiwana.
  > * Projekty są oparte na pliku project.json, które jest przestarzałe.
>
> Aby uzyskać więcej informacji na temat zmiany formatu projektu, zobacz [ogólny przegląd zmian](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Aby sprawdzić używanej wersji programu Visual Studio:
>
> * Na **pomocy** menu, wybierz **Microsoft Visual Studio**.
> * W **Microsoft Visual Studio** okno dialogowe, sprawdź numer wersji.
>   * W przypadku aplikacji .NET Core 3.0 w wersji zapoznawczej 3, Visual Studio 2019 wersji 16,0 lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 2.2 programu Visual Studio 2017 w wersji 15.9 lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 2.1 programu Visual Studio 2017 w wersji 15.7 lub nowszej.
>   * W przypadku aplikacji .NET Core 1.x programu Visual Studio 2017 w wersji 15,0 lub nowszej.
