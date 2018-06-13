---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, w zależności, należy na okien komputera do opracowywania i uruchamiania aplikacji .NET Core.
author: JRAlexander
ms.author: johalex
ms.date: 05/18/2018
ms.openlocfilehash: 3d172c83f0a79744afbaeeff52d7fea62d9b98b6
ms.sourcegitcommit: 895c7602386a6dfe7ca4facce3d965b27e5c6e87
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2018
ms.locfileid: "34311991"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie Windows

W tym artykule opisano zależności niezbędne do tworzenia aplikacji platformy .NET Core w systemie Windows. Obsługiwane wersje systemu operacyjnego i zależności, które należy wykonać dotyczą trzy sposoby tworzenia aplikacji platformy .NET Core w systemie Windows:

* [Wiersz polecenia](tutorials/using-with-xplat-cli.md)
* [Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)
* [Visual Studio Code](https://code.visualstudio.com/)

## <a name="net-core-supported-windows-versions"></a>Oprogramowanie .NET core obsługiwane wersje systemu Windows

Oprogramowanie .NET core jest obsługiwana w następujących wersjach:

* Windows 7 z dodatkiem SP1
* Windows 8.1
* Windows 10 Anniversary Update (w wersji 1607) lub nowszy
* Windows Server 2008 R2 z dodatkiem SP1 (całego serwera lub Server Core)
* Windows Server 2012 z dodatkiem SP1 (całego serwera lub Server Core)
* Windows Server 2012 R2 (całego serwera lub Server Core)
* Windows Server 2016 lub nowszy (całego serwera, Server Core lub Nano Server)

Następujące artykuły zawierają pełną listę .NET Core, obsługiwane systemy operacyjne dla poszczególnych wersji:

* [Oprogramowanie .NET core 2.1 — obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [Oprogramowanie .NET core 2.0 — obsługiwane wersje systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md)
* [.NET core 1.x — wersje obsługiwany system operacyjny](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

## <a name="net-core-dependencies"></a>Zależności .NET core

Podczas pracy z wersjami systemu Windows starszych niż Windows 10 i Windows Server 2016 .NET core 1.1 i wcześniejszych wersjach wymaga pakietu redystrybucyjnego Visual C++ Ta zależność jest automatycznie instalowany przez Instalatora platformy .NET Core.

[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:

* Instalowanie platformy .NET Core z [skryptu Instalatora](./tools/dotnet-install-script.md).
* Wdrażanie aplikacji .NET Core niezależne.
* Kompilowanie produktu ze źródła.
* Instalowanie platformy .NET Core za pomocą *.zip* pliku. Może to obejmować serwery kompilacji/CI/CD.

> [!NOTE]
> **Windows 8.1 i starszych wersjach, lub Windows Server 2012 R2 i wcześniejszych wersji:**
>
> Upewnij się, że instalacji systemu Windows jest aktualny i uwzględnia [KB2999226](https://support.microsoft.com/en-us/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za pomocą usługi Windows Update. Jeśli nie zainstalowano tę aktualizację, podczas uruchamiania aplikacji .NET Core zostanie wyświetlony błąd podobnie do następującej: `The program can't start because api-ms-win-crt-runtime-1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **W przypadku systemu Windows 7 lub Windows Server 2008 R2:**
>
> Oprócz KB2999226, upewnij się, masz również [KB2533623](https://support.microsoft.com/en-us/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) zainstalowane. Jeśli nie zainstalowano tę aktualizację, zostanie wyświetlone błąd podobny do następującego podczas uruchamiania aplikacji .NET Core: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-with-visual-studio-2017"></a>Wstępnie wymaganych składników w programie Visual Studio 2017 r.

Do tworzenia aplikacji platformy .NET Core przy użyciu zestawu SDK .NET Core, można użyć dowolnego edytora. [Visual Studio 2017](#visual-studio-2017) zapewnia zintegrowane środowisko deweloperskie dla aplikacji .NET Core w systemie Windows.

Więcej informacji na temat zmian w programie Visual Studio 2017 w [informacje o wersji](/visualstudio/releasenotes/vs2017-relnotes).

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Aby tworzyć aplikacje 2.x .NET Core w Visual Studio 2017:

 1. [Pobierz i zainstaluj program Visual Studio 2017 wersji 15.3.0 lub nowszej](/visualstudio/install/install-visual-studio) z **aplikacji dla wielu platform .NET Core** obciążenie (w **inne procesami** sekcji) wybrane.

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs-15-3-workloads.jpg)

Po **aplikacji dla wielu platform .NET Core** zestawu narzędzi jest zainstalowany, program Visual Studio 2017 używa .NET Core 1.x domyślnie. Zainstaluj oprogramowanie .NET Core 2.x zestaw SDK, aby uzyskać pomoc techniczną 2.x .NET Core w Visual Studio 2017 r.

 2. Zainstaluj [.NET Core 2.x SDK](https://www.microsoft.com/net/download/core).
 3. Przekieruj istniejące lub nowe projekty 1.x .NET Core do platformy .NET Core 2.x z poniższymi instrukcjami:
    * Na **projektu** menu, wybierz **właściwości**.
    * W **platformy docelowej** zaznaczenia menu, ustaw wartość na **.NET Core 2.0**.

![Zrzut ekranu programu Visual Studio 2017 aplikacji właściwości projektu z menu ".NET Core 2.0" docelowego framework wybranego elementu](./media/windows-prerequisites/Targeting-dotnetCore2.png)

Raz .NET Core 2.x zainstalowano zestaw SDK dla programu Visual Studio 2017 używa .NET Core SDK 2.x domyślnie i obsługuje następujące akcje:

* Otwórz kompilacji i uruchamianie istniejących projektów 1.x .NET Core.
* Przekierować projekty 1.x .NET Core 2.x, kompilacji i uruchom .NET Core.
* Utwórz nowe projekty 2.x .NET Core.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Do opracowywania aplikacji 1.x .NET Core w programie Visual Studio, [pobrać i zainstalować program Visual Studio 2017 RTM (wersja 15.0.26228.4) lub wyższej](/visualstudio/install/install-visual-studio) z **"Programowanie wieloplatformowych .NET Core"** obciążenie (w  **Inne procesami** sekcji) wybrane.

![Zrzut ekranu programu Visual Studio 2017 instalacji z obciążeniem "Programowanie wieloplatformowych .NET Core" wybrane](./media/windows-prerequisites/vs_workloads.jpg)

> [!IMPORTANT]
> Można użyć programu Visual Studio 2015 dla platformy .NET Core 1.x wdrożenia, ale nie jest zalecane z następujących powodów:
  > * Narzędzia .NET Core jest w wersji preview, która nie jest obsługiwana.
  > * Projekty są oparte na project.json, które jest przestarzałe.
>
> Aby uzyskać więcej informacji o zmianach format projektu, zobacz [ogólne omówienie zmiany](./tools/cli-msbuild-architecture.md).
---

> [!TIP]
> Aby sprawdzić swoją wersję programu Visual Studio 2017:
>
> * Na **pomocy** menu, wybierz **Microsoft Visual Studio**.
> * W **Microsoft Visual Studio** okna dialogowego, sprawdź numer wersji.
>   * W przypadku aplikacji .NET Core 2.1 RC programu Visual Studio 2017 wersji 15.7 lub nowszej.
>   * W przypadku aplikacji .NET Core 2.0, Visual Studio 2017 wersji 15.3 lub nowszej.
>   * W przypadku aplikacji .NET Core 1.x Visual Studio 2017 wersji 15,0 lub nowszej.
