---
title: "Wymagania wstępne dotyczące platformy .NET Core w systemie Windows"
description: "Dowiedz się, w zależności, należy na okien komputera do opracowywania i uruchamiania aplikacji .NET Core."
author: JRAlexander
ms.author: johalex
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: e64ecb807fd377458a9998ebbdfe2f6f15b115bb
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2018
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
* Windows Server 2016 (całego serwera, Server Core lub serwerze Nano)

Zobacz [.NET Core 2.x - obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pełną listę .NET Core 2.x obsługiwanych systemów operacyjnych.

Zobacz [1.x .NET Core obsługiwanych wersjach systemu operacyjnego](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md) pełną listę .NET Core 1.x obsługiwanych systemów operacyjnych.

## <a name="net-core-dependencies"></a>Zależności .NET core

Podczas pracy z wersjami systemu Windows starszych niż Windows 10 i Windows Server 2016 .NET core 1.1 i wcześniejszych wersjach wymaga pakietu redystrybucyjnego Visual C++ Ta zależność jest automatycznie instalowany przez Instalatora platformy .NET Core.

[Microsoft Visual C++ 2015 Redistributable Update 3](https://www.microsoft.com/download/details.aspx?id=52685) musi zostać zainstalowany ręcznie po:

* Instalowanie platformy .NET Core z [skryptu Instalatora](./tools/dotnet-install-script.md).
* Wdrażanie aplikacji .NET Core niezależne.
* Kompilowanie produktu ze źródła.
* Instalowanie platformy .NET Core za pomocą *.zip* pliku. Może to obejmować serwery kompilacji/CI/CD.

> [!NOTE]
> *Windows 7 i Windows Server 2008 tylko dla maszyn:* upewnij się, że instalacji systemu Windows jest aktualny i uwzględnia poprawkę [KB2533623](https://support.microsoft.com/help/2533623) zainstalowane za pomocą usługi Windows Update.

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
>   * W przypadku aplikacji 2.x .NET Core, programu Visual Studio 2017 wersji 15 ustęp 3 (26730.01) lub nowszej.
>   * W przypadku aplikacji 1.x .NET Core, programu Visual Studio 2017 wersji 15.0 (26228.04) lub nowszej.
