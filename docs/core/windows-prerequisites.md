---
title: Wymagania wstępne dotyczące platformy .NET Core w systemie Windows
description: Dowiedz się, jakie zależności są potrzebne na komputerze z systemem Windows, aby opracowywać i uruchamiać aplikacje platformy .NET Core.
f1_keywords:
- NETSDK1045
ms.custom: updateeachvsrelease
ms.date: 09/20/2019
ms.openlocfilehash: 6885f6c853efb0dcb2cb64b83f07e12b1dc2e3cf
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771956"
---
# <a name="prerequisites-for-net-core-on-windows"></a>Wymagania wstępne dotyczące platformy .NET Core w systemie Windows

W tym artykule przedstawiono obsługiwane wersje systemu operacyjnego w celu uruchamiania aplikacji platformy .NET Core w systemie Windows. Obsługiwane wersje systemu operacyjnego i zależności stosują się do trzech sposobów tworzenia aplikacji platformy .NET Core w systemie Windows:

* [Wiersz polecenia](./tutorials/using-with-xplat-cli.md)
* [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019)
* [Visual Studio Code](https://code.visualstudio.com/)

Ponadto, Jeśli opracowujesz system Windows przy użyciu programu Visual Studio, [wymagania wstępne dotyczące tworzenia aplikacji .NET Core za pomocą programu Visual Studio zawierają](#prerequisites-to-develop-net-core-apps-with-visual-studio) więcej szczegółów na temat minimalnych wersji obsługiwanych w przypadku programowania na platformie .NET Core.

## <a name="net-core-supported-operating-systems"></a>Obsługiwane systemy operacyjne .NET Core

Następujące artykuły zawierają pełną listę obsługiwanych systemów operacyjnych .NET Core na wersję:

* [.NET Core 3.0](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)
* [.NET Core 2,2](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)
* [.NET Core 2,1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)

Aby uzyskać linki do pobrania i więcej informacji, zobacz artykuł [pobieranie z platformy .NET](https://dotnet.microsoft.com/download) , aby pobrać najnowszą wersję lub [archiwum pobierania programu .NET](https://dotnet.microsoft.com/download/archives#dotnet-core) dla starszych wersji.

## <a name="net-core-dependencies"></a>Zależności .NET Core

[Pakiet redystrybucyjny Microsoft Visual C++ 2015 z aktualizacją Update 3](https://www.microsoft.com/download/details.aspx?id=52685) należy zainstalować ręcznie, gdy:

* Instalowanie programu .NET Core za pomocą [skryptu Instalatora](./tools/dotnet-install-script.md).
* Wdrażanie samodzielnej aplikacji .NET Core.
* Kompilowanie produktu ze źródła.
* Instalowanie platformy .NET Core za pośrednictwem pliku *. zip* . Może to obejmować serwery kompilacji/ciągłej integracji/ciągłego wdrażania.

> [!NOTE]
> **W przypadku Windows 8.1 i starszych wersji lub systemu Windows Server 2012 R2 i starszych wersji:**
>
> Upewnij się, że instalacja systemu Windows jest aktualna i zawiera [KB2999226](https://support.microsoft.com/help/2999226/update-for-universal-c-runtime-in-windows), które można zainstalować za Windows Update. Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji .NET Core zobaczysz błąd podobny do poniższego: `The program can't start because api-ms-win-crt-runtime-l1-1-0.dll is missing from your computer. Try reinstalling the program to fix this problem.`
>
> **Dla systemu Windows 7 lub Windows Server 2008 R2:**
>
> Oprócz KB2999226 upewnij się, że zainstalowano również [poprawki KB2533623](https://support.microsoft.com/help/2533623/microsoft-security-advisory-insecure-library-loading-could-allow-remot) . Jeśli ta aktualizacja nie została zainstalowana, podczas uruchamiania aplikacji .NET Core zostanie wyświetlony komunikat o błędzie podobny do poniższego: `The library hostfxr.dll was found, but loading it from C:\<path_to_app>\hostfxr.dll failed`.

## <a name="prerequisites-to-develop-net-core-apps-with-visual-studio"></a>Wymagania wstępne dotyczące opracowywania aplikacji platformy .NET Core za pomocą programu Visual Studio

Mimo że można użyć dowolnego edytora do tworzenia aplikacji platformy .NET Core przy użyciu zestaw .NET Core SDK, program Visual Studio 2017 i jego nowsze wersje zapewniają zintegrowane środowisko programistyczne dla aplikacji platformy .NET Core w systemie Windows.

<a name="vs-mapping"></a>

Każda wersja programu .NET Core ma wymaganą minimalną wersję programu Visual Studio. Aby sprawdzić wersję programu Visual Studio:

* W menu **Pomoc** wybierz pozycję **informacje Microsoft Visual Studio**.
* W oknie dialogowym **Informacje o Microsoft Visual Studio** Sprawdź numer wersji.

W poniższej tabeli wymieniono minimalną wersję każdego zestawu SDK:

| Wersja zestaw .NET Core SDK | Wersja programu Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.0                   | Program Visual Studio 2019 w wersji 16,3 lub nowszej. |
| 2,2                   | Program Visual Studio 2017 w wersji 15,9 lub nowszej. |
| 2,1                   | Program Visual Studio 2017 w wersji 15,7 lub nowszej. |
| 1.x                   | Program Visual Studio 2017 w wersji 15,0 lub nowszej. |

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2019 przy użyciu zestawu SDK programu .NET Core 3,0:

* [Pobierz i zainstaluj program Visual Studio 2019 w wersji 16,3 lub nowszej](/visualstudio/install/install-visual-studio) i wybierz jedno z następujących obciążeń, które zawierają zestaw .NET Core SDK, w zależności od rodzaju kompilowanej aplikacji:

  * Obciążenie **Międzyplatformowe dla platformy .NET Core** w sekcji **inne zestawy narzędzi** .
  * **ASP.NET i programowanie w sieci Web** w sekcji **chmury & sieci Web** .
  * Obciążenie **programowaniem pulpitu sieciowego** w sekcji **systemu Windows** .

Na poniższej ilustracji przedstawiono obciążenie **Międzyplatformowe platformy .NET Core** wybrane w interfejsie użytkownika programu Visual Studio:

![Zrzut ekranu instalacji programu Visual Studio 2019 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2019-workloads.jpg)

Program Visual Studio 2019 w wersji 16,3 domyślnie używa programu .NET Core 3,0 SDK po zainstalowaniu dowolnego z tych obciążeń.

Jeśli chcesz, aby istniejące projekty korzystały z najnowszego środowiska uruchomieniowego platformy .NET Core, Przekieruj każdy istniejący projekt .NET Core do programu .NET Core 3,0, korzystając z następujących instrukcji:

* W menu **projekt** wybierz polecenie **Właściwości**.
* W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 3,0**.

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2019 z wybranym elementem menu platformy docelowej ".NET Core 3,0"](./media/windows-prerequisites/target-dotnet-core-3-0.jpg)

Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 3,0 można wykonać następujące czynności:

* Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.
* Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 3,0, kompilacji i uruchomienia.
* Utwórz nowe projekty platformy .NET Core 3,0.

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

Aby tworzyć aplikacje platformy .NET Core w programie Visual Studio 2017 przy użyciu zestawu SDK programu .NET Core 2,2:

* [Pobierz i zainstaluj program Visual Studio 2019 w wersji 16,3 lub nowszej](/visualstudio/install/install-visual-studio) przy użyciu obciążenia **międzyplatformowego platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).
* [Pobierz i zainstaluj program Visual Studio 2017 w wersji 15.9.0 lub nowszej](/visualstudio/install/install-visual-studio) z wybranym obciążeniem **międzyplatformowym platformy .NET Core** (w sekcji **inne zestawy narzędzi** ).

![Zrzut ekranu instalacji programu Visual Studio 2017 z wybranym obciążeniem "Programowanie dla wielu platform" platformy .NET Core](./media/windows-prerequisites/vs-2017-workloads.jpg)

Po zainstalowaniu zestawu narzędzi do **tworzenia aplikacji dla wielu platform platformy .NET Core** program Visual Studio zwykle instaluje poprzednią wersję zestaw .NET Core SDK.
Na przykład program Visual Studio 2017 w wersji 15,9 domyślnie używa programu .NET Core 2,1 SDK po zainstalowaniu obciążenia.

Aby zaktualizować program Visual Studio do korzystania z zestawu SDK programu .NET Core 2,2:

 1. Zainstaluj [zestaw SDK platformy .NET Core 2,2](https://dotnet.microsoft.com/download).

 1. Jeśli chcesz, aby projekt używał najnowszej wersji środowiska uruchomieniowego platformy .NET Core, Przekieruj każdy istniejący lub nowy projekt .NET Core do programu .NET Core 2,2, korzystając z następujących instrukcji:

    * W menu **projekt** wybierz polecenie **Właściwości**.
    * W menu wyboru **platformy docelowej** ustaw wartość na **.NET Core 2,2**.

![Zrzut ekranu przedstawiający właściwość projektu aplikacji programu Visual Studio 2017 z wybranym elementem menu platformy docelowej ".NET Core 2,2"](./media/windows-prerequisites/targeting-dotnet-core.jpg)

Po skonfigurowaniu programu Visual Studio przy użyciu zestawu SDK platformy .NET Core 2,2 można wykonać następujące czynności:

* Otwórz, skompiluj i uruchom istniejące projekty platformy .NET Core 1. x i 2. x.
* Przekieruj projekty platformy .NET Core 1. x i 2. x do platformy .NET Core 2,2, kompilacji i uruchomienia.
* Utwórz nowe projekty platformy .NET Core 2,2.

---
