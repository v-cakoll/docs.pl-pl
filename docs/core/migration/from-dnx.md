---
title: Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core
description: Przeprowadź migrację z używania narzędzi środowiska DNX, aby interfejs wiersza polecenia platformy .NET Core narzędzia.
ms.date: 06/20/2016
ms.openlocfilehash: 31317f110ae1e8586b78becd757d0a8ff07f1459
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503818"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core (Project. JSON)

## <a name="overview"></a>Omówienie
W wersji RC1 oprogramowania .NET Core i ASP.NET Core 1,0 wprowadzono narzędzia środowiska DNX. Wersja RC2 oprogramowania .NET Core i ASP.NET Core 1,0 została przeniesiona z środowiska DNX do interfejs wiersza polecenia platformy .NET Core.

Jako niewielki odświeżacz, przyjrzyjmy się podsumowanie środowiska DNX. ŚRODOWISKA DNX to środowisko uruchomieniowe i zestaw narzędzi służący do tworzenia aplikacji .NET Core i, w ASP.NET Core 1,0. Składają się z 3 głównych elementów:

1. DNVM — skrypt instalacyjny do uzyskania środowiska DNX
2. ŚRODOWISKA DNX (środowisko uruchomieniowe programu dotnet) — środowisko uruchomieniowe wykonujące kod
3. DNU (Narzędzie programistyczne dotnet) — narzędzia do zarządzania zależnościami, kompilowania i publikowania aplikacji

Po wprowadzeniu interfejsu wiersza polecenia wszystkie powyższe elementy są teraz częścią jednego zestawu narzędzi. Jednak ponieważ środowiska DNX był dostępny w okresie RC1, można utworzyć projekty, które zostały skompilowane przy użyciu go, aby przenieść je do nowego narzędzia interfejsu wiersza polecenia.

Ten przewodnik migracji obejmuje podstawowe informacje na temat migrowania projektów z środowiska DNX i do interfejs wiersza polecenia platformy .NET Core. Jeśli dopiero zaczynasz projekt od podstaw .NET Core, możesz swobodnie pominąć ten dokument.

## <a name="main-changes-in-the-tooling"></a>Główne zmiany w narzędziach
Istnieją pewne ogólne zmiany w narzędziach, które powinny być opisane w pierwszej kolejności.

### <a name="no-more-dnvm"></a>Nie ma więcej DNVM
DNVM, Short for *dotnet Version Manager* to skrypt bash/PowerShell służący do instalowania środowiska DNX na komputerze. Umożliwia to użytkownikom uzyskanie potrzebnych przez nich środowiska DNX z określonych przez siebie kanałów informacyjnych (lub ich domyślnych), a także oznaczenie niektórych środowiska DNX "Active", co spowodowałoby umieszczenie go w $PATH dla danej sesji. Pozwoli to na korzystanie z różnych narzędzi.

DNVM została wycofana, ponieważ jej zestaw funkcji został wykonany nadmiarowy przez zmiany wprowadzone w interfejs wiersza polecenia platformy .NET Core.

Interfejs wiersza polecenia jest spakowany na dwa sposoby:

1. Natywne Instalatory dla danej platformy
2. Skrypt instalacji dla innych sytuacji (takich jak serwery CI)

Z tego względu nie trzeba instalować funkcji instalacji DNVM. Ale co z funkcjami wyboru środowiska uruchomieniowego?

Odwołanie do środowiska uruchomieniowego w `project.json` przez dodanie pakietu określonej wersji do zależności. W przypadku tej zmiany aplikacja będzie mogła korzystać z nowych bitów środowiska uruchomieniowego. Pobieranie tych bitów na maszynę jest takie samo jak w przypadku interfejsu wiersza polecenia: instalujesz środowisko uruchomieniowe za pośrednictwem jednego z natywnych instalatorów, które obsługuje lub za pośrednictwem jego skryptu instalacji.

### <a name="different-commands"></a>Różne polecenia
Jeśli używasz środowiska DNX, używasz niektórych poleceń z jednej z trzech części (środowiska DNX, DNU lub DNVM). W interfejsie wiersza polecenia niektóre z tych poleceń uległy zmianie, niektóre nie są dostępne i niektóre są takie same, ale mają nieco inną semantykę.

W poniższej tabeli przedstawiono mapowanie między poleceniami środowiska DNX/DNU i ich odpowiednikami interfejsu wiersza.

| ŚRODOWISKA DNX — polecenie                    | Interfejs wiersza polecenia    | Opis                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| środowiska DNX                        | `dotnet run`     | Uruchom kod ze źródła.                                                                                           |
| Kompilacja dnu                      | `dotnet build`   | Kompiluj plik binarny IL w kodzie.                                                                                |
| Pakiet dnu                       | `dotnet pack`    | Pakuj pakiet NuGet kodu.                                                                        |
| środowiska DNX \[polecenie] (na przykład "środowiska DNX Web") | Nie dotyczy\*          | W środowiska DNX świecie Uruchom polecenie zgodnie z definicją w pliku Project. JSON.                                                     |
| dnu Zainstaluj                    | Nie dotyczy\*          | Na świecie środowiska DNX Zainstaluj pakiet jako zależność.                                                            |
| dnu przywracanie                    | `dotnet restore` | Przywróć zależności określone w pliku Project. JSON. ([Zobacz Uwaga](#dotnet-restore-note))                                                            |
| dnu publikowanie                    | `dotnet publish` | Publikowanie aplikacji do wdrożenia w jednej z trzech formularzy (przenośne, przenośne z natywną i autonomiczną). |
| Zawijanie dnu                       | Nie dotyczy\*          | W środowiska DNX świecie zawiń plik Project. JSON w csproj.                                                                    |
| polecenia dnu                   | Nie dotyczy\*          | W środowiska DNX świecie Zarządzaj poleceniami zainstalowanymi globalnie.                                                           |

(\*) — te funkcje nie są obsługiwane w interfejsie wiersza polecenia przez zaprojektowanie.

## <a name="dnx-features-that-are-not-supported"></a>Nieobsługiwane funkcje środowiska DNX
Jak przedstawiono w powyższej tabeli, istnieją funkcje z świata środowiska DNX, które nie podjęły pomocy technicznej w interfejsie wiersza polecenia, co najmniej przez czas. Ta sekcja zawiera najważniejsze elementy i pozwala racjonalne uzasadnienie, a także obejść, jeśli są potrzebne.

### <a name="global-commands"></a>Polecenia globalne
DNU został dostarczony z koncepcją o nazwie "polecenia globalne". Są to głównie aplikacje konsolowe spakowane jako pakiety NuGet przy użyciu skryptu powłoki, który wywoła środowiska DNX określony do uruchamiania aplikacji.

Interfejs wiersza polecenia nie obsługuje tego pojęcia. Jednak jest to obsługiwane przez Dodawanie poleceń dla projektu, które mogą być wywoływane przy użyciu znanej składni `dotnet <command>`.

### <a name="installing-dependencies"></a>Instalowanie zależności
Począwszy od wersji 1 interfejs wiersza polecenia platformy .NET Core nie ma `install` polecenia do instalowania zależności. Aby można było zainstalować pakiet z programu NuGet, należy go dodać jako zależność do pliku `project.json`, a następnie uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)).

### <a name="running-your-code"></a>Uruchamianie kodu
Istnieją dwa podstawowe sposoby uruchamiania kodu. Jeden z nich pochodzi ze źródła z `dotnet run`. W przeciwieństwie do `dnx run`, nie będzie to żadnej kompilacji w pamięci. Faktycznie wywoła `dotnet build`, aby skompilować kod, a następnie uruchomić skompilowany plik binarny.

Innym sposobem jest użycie `dotnet` samego do uruchomienia kodu. Jest to realizowane przez podanie ścieżki do zestawu: `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrowanie projektu środowiska DNX do interfejs wiersza polecenia platformy .NET Core
Oprócz korzystania z nowych poleceń podczas pracy z kodem, istnieją trzy główne rzeczy do migracji z środowiska DNX:

1. Migruj plik `global.json`, jeśli masz możliwość korzystania z interfejsu wiersza polecenia.
2. Migrowanie pliku projektu (`project.json`) do narzędzia interfejsu wiersza polecenia.
3. Migrowanie dowolnych interfejsów API środowiska DNX do ich odpowiedników BCL.

### <a name="changing-the-globaljson-file"></a>Zmiana pliku Global. JSON
Plik `global.json` działa jak plik rozwiązania dla projektów RC1 i RC2 (lub nowszych). Aby interfejs wiersza polecenia platformy .NET Core (jak również program Visual Studio) do rozróżniania między wersjami RC1 i nowszymi, używają właściwości `"sdk": { "version" }`, aby ustalić, który projekt jest w wersji RC1 lub nowszej. Jeśli `global.json` nie ma tego węzła, zakłada się, że jest to najnowsza wartość.

Aby zaktualizować plik `global.json`, Usuń właściwość lub ustaw ją na dokładną wersję narzędzi, których chcesz użyć, w tym przypadku **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrowanie pliku projektu

Interfejs wiersza polecenia i środowiska DNX używają tego samego podstawowego systemu projektu opartego na pliku `project.json`. Składnia i semantyka pliku projektu są znacznie takie same, z małymi różnicami w zależności od scenariuszy. Istnieją także pewne zmiany schematu, które można wyświetlić w [pliku schematu](http://json.schemastore.org/project).

Jeśli tworzysz aplikację konsolową, musisz dodać następujący fragment kodu do pliku projektu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

To instruuje `dotnet build`, aby emitować punkt wejścia dla aplikacji, efektywnie czyniąc kod możliwy do uruchomienia. Jeśli tworzysz bibliotekę klas, po prostu Pomiń powyższą sekcję. Oczywiście po dodaniu powyższego fragmentu kodu do pliku `project.json` należy dodać statyczny punkt wejścia. Po przejściu na środowiska DNX usługi DI usług, które podano, nie są już dostępne i dlatego musi być podstawowym punktem wejścia platformy .NET: `static void Main()`.

Jeśli masz sekcję "polecenia" w `project.json`, możesz ją usunąć. Niektóre z poleceń, które były używane jako polecenia DNU, takie jak polecenia interfejsu CLI Entity Framework, są przyłączone do rozszerzeń dla poszczególnych projektów do interfejsu wiersza polecenia. Jeśli utworzono własne polecenia, które są używane w projektach, należy je zastąpić przy użyciu rozszerzeń interfejsu wiersza polecenia. W takim przypadku węzeł `commands` w `project.json` musi zostać zastąpiony przez węzeł `tools` i musi on zawierać listę zależności narzędzi.

Po wykonaniu tych czynności należy zdecydować, który typ przenośności ma być używany przez aplikację. W przypadku platformy .NET Core zainwestowano w celu udostępnienia spektrum opcji przenoszenia, spośród których można dokonać wyboru. Na przykład może być konieczne posiadanie w pełni *przenośnej* *aplikacji lub aplikacji.* Opcja aplikacji przenośnej jest większa, podobnie jak .NET Framework aplikacje: potrzebuje składnika współużytkowanego, aby wykonać go na maszynie docelowej (.NET Core). Aplikacja samodzielna nie wymaga zainstalowania platformy .NET Core na serwerze docelowym, ale konieczne jest utworzenie jednej aplikacji dla każdego systemu operacyjnego, który ma być obsługiwany. Te typy przenośności i inne zostały omówione w dokumencie [Typ przenośności aplikacji](../deploying/index.md) .

Po nawiązaniu połączenia z typem potrzebnego przenośności należy zmienić planowane platformy. Jeśli zapisząsz aplikacje dla platformy .NET Core, najprawdopodobniej używasz `dnxcore50` jako platformy dostosowanej. Przy użyciu interfejsu wiersza polecenia i zmian wprowadzonych przez nowy [.NET Standard](../../standard/net-standard.md) , struktura musi być jedną z następujących:

1. `netcoreapp1.0` — Jeśli piszesz aplikacje w programie .NET Core (w tym aplikacje ASP.NET Core)
2. `netstandard1.6` — w przypadku pisania bibliotek klas dla platformy .NET Core

Jeśli używasz innych obiektów docelowych `dnx`, takich jak `dnx451`, musisz również zmienić te elementy. `dnx451` należy zmienić na `net451`.
Aby uzyskać więcej informacji, zapoznaj się z tematem [.NET Standard](../../standard/net-standard.md) .

`project.json` jest teraz głównie gotowa. Musisz przejść przez listę zależności i zaktualizować zależności do ich nowszych wersji, zwłaszcza jeśli używasz zależności ASP.NET Core. Jeśli używasz oddzielnych pakietów dla interfejsów API BCL, możesz użyć pakietu środowiska uruchomieniowego, jak wyjaśniono w dokumencie [Typ przenośności aplikacji](../deploying/index.md) .

Gdy wszystko będzie gotowe, możesz spróbować wykonać przywracanie z `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)). W zależności od wersji zależności mogą wystąpić błędy, jeśli NuGet nie może rozpoznać zależności dla jednej z powyższych platform. Jest to problem "punkt-czas"; wraz z przekroczeniem czasu, więcej i więcej pakietów będzie obejmować obsługę tych platform. Na razie w przypadku uruchomienia tego programu można użyć instrukcji `imports` w węźle `framework`, aby określić NuGet, że może przywrócić pakiety przeznaczone dla platformy w ramach instrukcji "Imports".
Błędy przywracania, które otrzymujesz w tym przypadku, powinny zapewnić wystarczającą ilość informacji, aby określić, które platformy należy zaimportować. W przypadku niewielkiego zgubienia lub nowego do tego, ogólnie rzecz biorąc, określ `dnxcore50` i `portable-net45+win8` w instrukcji `imports` powinna to być lewę. Poniższy fragment kodu JSON pokazuje, jak wygląda:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Uruchomienie `dotnet build` spowoduje wyświetlenie ewentualnych błędów kompilacji, chociaż nie powinna istnieć zbyt wiele z nich. Po skompilowaniu i prawidłowym uruchomieniu kodu możesz go przetestować przy użyciu modułu uruchamiającego. Wykonaj `dotnet <path-to-your-assembly>` i zobacz, jak to działa.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
