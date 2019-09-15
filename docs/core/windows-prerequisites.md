---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, jakie zależności są potrzebne na komputerze z systemem Windows, aby opracowywać i uruchamiać aplikacje platformy .NET Core.
ms.custom: updateeachvsrelease
ms.date: 04/08/2019
ms.openlocfilehash: 7b2bf2b8353c4f02fa11e9e7531e0d936007be0b
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970287"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie Windows

W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji platformy .NET Core w systemie Windows. Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core w systemie Windows:

* [Wiersz polecenia](tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)
* [Visual Studio Code](https://code.visualstudio.com/)

Ponadto, Jeśli opracowujesz system Windows przy użyciu programu Visual Studio 2017, [wymagania wstępne dotyczące programu Visual studio 2017 zawierają](#prerequisites-with-visual-studio-2017) więcej szczegółów na temat minimalnej wersji, które są obsługiwane w przypadku programowania na platformie .NET Core.

## <a name="net-core-supported-operating-systems"></a>Obsługiwane systemy operacyjne .NET Core

Następujące artykuły zawierają pełną listę obsługiwanych systemów operacyjnych .NET Core na wersję:

* [.NET Core 3,0 (wersja zapoznawcza)](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2.2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)
* [.NET Core 1.0](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)

Aby uzyskać linki do pobrania i więcej informacji, zobacz artykuł [pobieranie z platformy .NET](https://dotnet.microsoft.com/download) , aby pobrać najnowszą wersję lub [archiwum pobierania programu .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.

## <a name="net-core-dependencies"></a>Zależności .NET Core

Program .NET Core 1,1 i jego wcześniejsze wersje wymagają C++ , aby pakiet redystrybucyjny wizualizacji był uruchamiany w wersjach systemu Windows starszych niż Windows 10 i windows Server 2016. Ta zależność jest automatycznie instalowana przez Instalatora .NET Core.

[Pakiet redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685) należy zainstalować ręcznie, gdy:

* Instalowanie programu .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).
* Wdrażanie samodzielnej aplikacji .NET Core.
* Kompilowanie produktu ze źródła.
* Instalowanie platformy .NET Core za pośrednictwem pliku *. zip* . Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.

> [!NOTE]
> **W przypadku Windows 8.1 i starszych wersji lub systemu Windows Server 2012 R2 i starszych wersji:**
>
> Upewnij się, że instalacja systemu Windows jest aktualna i zawiera [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za Windows Update. Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji .NET Core zobaczysz błąd podobny do poniższego:`The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Dla systemu Windows 7 lub Windows Server 2008 R2:**
>
> Oprócz KB2999226 upewnij się, że zainstalowano również [poprawki KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) . Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji platformy .NET Core zobaczysz błąd podobny do poniższego: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-for-net-core-30-preview-3"></a>Wymagania wstępne dotyczące programu .NET Core 3,0 (wersja zapoznawcza 3)

Program .NET Core 3,0 w wersji zapoznawczej 3 ma takie same wymagania wstępne jak w przypadku innych wersji programu .NET Core. Jeśli jednak chcesz użyć programu Visual Studio do tworzenia projektów platformy .NET Core 3,0, musisz użyć programu [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019). Program Visual Studio 2019 można zainstalować równolegle z innymi wersjami programu Visual Studio bez konfliktu.

## <a name="prerequisites-with-visual-studio-2017"></a>Wymagania wstępne dotyczące programu Visual Studio 2017
    
Za pomocą dowolnego edytora można opracowywać aplikacje platformy .NET Core przy użyciu zestaw .NET Core SDK. Program Visual Studio 2017 zapewnia zintegrowane środowisko programistyczne dla aplikacji platformy .NET Core w systemie Windows.

Więcej informacji o zmianach w programie Visual Studio 2017 można znaleźć w [informacjach o wersji](/visualstudio/releasenotes/vs2017-relnotes).

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu SDK programu .NET Core 2,2:

 1. [Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z wybranym obciążeniem międzyplatformowym **platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po zainstalowaniu zestawu narzędzi do **tworzenia aplikacji dla wielu platform platformy .NET Core** program Visual Studio zwykle instaluje poprzednią wersję zestaw .NET Core SDK.
Na przykład program Visual Studio 2017 15,9 domyślnie używa programu .NET Core 2,1 SDK po zainstalowaniu obciążenia.

Aby zaktualizować program Visual Studio do korzystania z zestawu SDK programu .NET Core 2,2:

 1. Zainstaluj [zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download).

 1. Jeśli chcesz, aby projekt używał najnowszej wersji środowiska uruchomieniowego platformy .NET Core, Przekieruj istniejące lub nowe projekty platformy .NET Core do programu .NET Core 2,2, korzystając z następujących instrukcji:

    * W menu **projekt** wybierz polecenie **Właściwości**.
    * W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 2,2**.

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2017 z wybranym elementem menu platformy docelowej ".NET Core 2,2"](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 2,2 można wykonać następujące czynności:

* Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.
* Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 2,2, kompilacji i uruchomienia.
* Utwórz nowe projekty platformy .NET Core 2,2.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

Aby opracowywać aplikacje platformy .NET Core 1. x w programie Visual Studio, [Pobierz i zainstaluj program Visual Studio 2017](/visualstudio/install/install-visual-studio) z użyciem obciążenia międzyplatformowego dla **platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-workloads.jpg)

> [!IMPORTANT]
> Możliwe jest korzystanie z programu Visual Studio 2015 do programowania w środowisku .NET Core 1. x, ale nie jest to zalecane z następujących powodów:
>
> * Narzędzia .NET Core są w wersji zapoznawczej, która nie jest obsługiwana.
> * Projekty to oparte na pliku Project. JSON, które jest przestarzałe.
>
> Aby uzyskać więcej informacji na temat zmian w formacie projektu, zobacz [Ogólne omówienie zmian](./tools/cli-msbuild-architecture.md).

---

<a name="vs-mapping"></a>

> [!TIP]
> Aby sprawdzić wersję programu Visual Studio:
>
> * W menu **Pomoc** wybierz pozycję **informacje Microsoft Visual Studio**.
> * W oknie dialogowym **Informacje o Microsoft Visual Studio** Sprawdź numer wersji.
>   * W przypadku aplikacji .NET Core 3,0 Preview 3, Visual Studio 2019 w wersji 16,0 lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 2,2 program Visual Studio 2017 w wersji 15,9 lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 2,1 program Visual Studio 2017 w wersji 15,7 lub nowszej.
>   * W przypadku aplikacji platformy .NET Core 1. x program Visual Studio 2017 w wersji 15,0 lub nowszej.
