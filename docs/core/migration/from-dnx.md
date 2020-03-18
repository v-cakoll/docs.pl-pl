---
title: Migracja z pliku DNX do procesora CLI programu .NET Core
description: Migracja z użyciem narzędzi DNX do narzędzi cli .NET Core.
ms.date: 06/20/2016
ms.openlocfilehash: 31317f110ae1e8586b78becd757d0a8ff07f1459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503818"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migracja z dnx do .NET Core CLI (project.json)

## <a name="overview"></a>Omówienie
Wydanie RC1 .NET Core i ASP.NET Core 1.0 wprowadziło oprzyrządowanie DNX. Wersja RC2 .NET Core i ASP.NET Core 1.0 została przeniesiona z DNX do .NET Core CLI.

Jako niewielkie odświeżanie, podsumujmy, o co chodziło DNX. DNX był zestawem runtime i narzędzi używanym do tworzenia .NET Core, a dokładniej ASP.NET aplikacji Core 1.0. Składał się z 3 głównych elementów:

1. DNVM - skrypt instalujący do uzyskiwania DNX
2. DNX (Dotnet Wykonanie runtime) — czas wykonywania, który wykonuje kod
3. DNU (Dotnet Developer Utility) - narzędzia do zarządzania zależnościami, tworzenia i publikowania aplikacji

Wraz z wprowadzeniem cli, wszystkie powyższe są teraz częścią jednego zestawu narzędzi. Jednak ponieważ DNX był dostępny w ramach czasowych RC1, może być projekty, które zostały zbudowane przy użyciu go, które chcesz przejść do nowego narzędzia CLI.

Ten przewodnik migracji obejmie podstawowe informacje dotyczące migracji projektów z dnx i na .NET Core CLI. Jeśli dopiero zaczynasz projekt na .NET Core od podstaw, możesz swobodnie pominąć ten dokument.

## <a name="main-changes-in-the-tooling"></a>Główne zmiany w oprzyrządowaniu
Istnieją pewne ogólne zmiany w narzędzi, które powinny być opisane w pierwszej kolejności.

### <a name="no-more-dnvm"></a>Koniec z DNVM
DNVM, skrót od *DotNet Version Manager* był bash/PowerShell skrypt używany do instalowania DNX na komputerze. To pomogło użytkownikom uzyskać DNX, których potrzebują z pliku danych, które określiły (lub domyślne), a także oznaczyć pewne DNX "aktywny", który umieściłby go na $PATH dla danej sesji. Pozwoliłoby to na korzystanie z różnych narzędzi.

DNVM został przerwany, ponieważ jego zestaw funkcji został zbędny przez zmiany nadchodzące w .NET Core CLI.

CLI jest pakowany na dwa główne sposoby:

1. Instalatorzy natywni dla danej platformy
2. Instalowanie skryptu w innych sytuacjach (np. serwery ci)

Biorąc to pod uwagę, funkcje instalacji DNVM nie są potrzebne. Ale co z funkcjami wyboru czasu wykonywania?

Odwołujesz się do `project.json` witryny uruchomieniowej w swoim, dodając pakiet określonej wersji do zależności. Dzięki tej zmianie aplikacja będzie mogła używać nowych bitów czasu wykonywania. Wprowadzenie tych bitów do komputera jest taka sama jak w przypadku identyfikatora CLI: instalujesz czas uruchomieniowy za pośrednictwem jednego z natywnych instalatorów, które obsługuje lub za pośrednictwem skryptu instalowania.

### <a name="different-commands"></a>Różne polecenia
Jeśli używasz DNX, użyto niektórych poleceń z jednej z jego trzech części (DNX, DNU lub DNVM). W poszczególnych wierszach polecenia niektóre z tych poleceń zmieniają się, niektóre nie są dostępne, a niektóre są takie same, ale mają nieco inną semantykę.

W poniższej tabeli przedstawiono mapowanie między poleceniami DNX/DNU a ich odpowiednikami cli.

| DNX, polecenie                    | Polecenie CLI    | Opis                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| bieg dnx                        | `dotnet run`     | Uruchom kod ze źródła.                                                                                           |
| kompilacja dnu                      | `dotnet build`   | Zbuduj il binarny kodu.                                                                                |
| pakiet dnu                       | `dotnet pack`    | Spakować pakiet NuGet kodu.                                                                        |
| dnx] \[(na przykład "dnx web") | Nie dotyczy\*          | W świecie DNX uruchom polecenie zgodnie z definicją w project.json.                                                     |
| instalacja dnu                    | Nie dotyczy\*          | W świecie DNX zainstaluj pakiet jako zależność.                                                            |
| przywracanie dnu                    | `dotnet restore` | Przywracanie zależności określonych w programie project.json. ([patrz uwaga](#dotnet-restore-note))                                                            |
| dnu publikować                    | `dotnet publish` | Opublikuj aplikację do wdrożenia w jednym z trzech formularzy (przenośnych, przenośnych z natywnych i autonomicznych). |
| zawijanie dnu                       | Nie dotyczy\*          | W świecie DNX, owinąć project.json w csproj.                                                                    |
| polecenia dnu                   | Nie dotyczy\*          | W świecie DNX zarządzaj globalnie zainstalowanymi poleceniami.                                                           |

(\*) - te funkcje nie są obsługiwane w CLI zgodnie z projektem.

## <a name="dnx-features-that-are-not-supported"></a>Funkcje DNX, które nie są obsługiwane
Jak pokazuje powyższa tabela, istnieją funkcje ze świata DNX, których zdecydowaliśmy się nie obsługiwać w cli, przynajmniej na razie. Ta sekcja przejdzie przez najważniejsze z nich i określi uzasadnienie, dla którego nie wspierają ich, a także obejścia, jeśli ich potrzebujesz.

### <a name="global-commands"></a>Polecenia globalne
DNU przyszedł z pojęciem o nazwie "poleceń globalnych". Były to zasadniczo aplikacje konsoli spakowane jako pakiety NuGet ze skryptem powłoki, który wywoływałby DNX określony do uruchamiania aplikacji.

CLI nie obsługuje tej koncepcji. Obsługuje jednak koncepcję dodawania poleceń dla projektu, które mogą być `dotnet <command>` wywoływane przy użyciu znanej składni.

### <a name="installing-dependencies"></a>Instalowanie zależności
W przypadku systemu v1 polecenie CLI programu `install` .NET Core nie ma polecenia instalowania zależności. Aby zainstalować pakiet z NuGet, należy dodać go jako zależność `project.json` do pliku, a następnie uruchomić `dotnet restore` [(zobacz uwaga).](#dotnet-restore-note)

### <a name="running-your-code"></a>Uruchamianie kodu
Istnieją dwa główne sposoby uruchamiania kodu. Jeden jest ze `dotnet run`źródła, z . W `dnx run`przeciwieństwie do tego, nie spowoduje to kompilacji w pamięci. Będzie faktycznie wywołać `dotnet build` do tworzenia kodu, a następnie uruchomić wbudowany binarny.

Innym sposobem jest `dotnet` użycie samego do uruchomienia kodu. Odbywa się to poprzez zapewnienie ścieżki `dotnet path/to/an/assembly.dll`do zestawu: .

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrowanie projektu DNX do .NET Core CLI
Oprócz używania nowych poleceń podczas pracy z kodem, istnieją trzy główne rzeczy w migracji z DNX:

1. Migruj `global.json` plik, jeśli masz go, aby móc używać funkcji CLI.
2. Migrowanie samego`project.json`pliku projektu ( ) do narzędzi CLI.
3. Migrowanie z wszelkich interfejsów API DNX do ich odpowiedników BCL.

### <a name="changing-the-globaljson-file"></a>Zmiana pliku global.json
Plik `global.json` działa jak plik rozwiązania zarówno dla RC1 i RC2 (lub nowszych) projektów. Aby .NET Core CLI (a także Visual Studio) do rozróżniania rc1 i nowszych wersji, używają `"sdk": { "version" }` właściwości, aby rozróżnić, który projekt rc1 lub nowszych. Jeśli `global.json` nie ma tego węzła w ogóle, zakłada się, że jest najnowszy.

Aby zaktualizować `global.json` plik, usuń właściwość lub ustaw ją na dokładną wersję narzędzi, których chcesz użyć, w tym przypadku **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrowanie pliku projektu

Zarówno cli, jak i DNX używają `project.json` tego samego podstawowego systemu projektu opartego na pliku. Składnia i semantyka pliku projektu są prawie takie same, z niewielkimi różnicami opartymi na scenariuszach. Istnieją również pewne zmiany w schemacie, które można zobaczyć w [pliku schematu](http://json.schemastore.org/project).

Jeśli używasz aplikacji konsoli, musisz dodać następujący fragment kodu do pliku projektu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Spowoduje to `dotnet build` elokwaty, aby emitować punkt wejścia dla aplikacji, skutecznie dzięki czemu kod będzie można uruchomić. Jeśli budujesz bibliotekę klas, po prostu pomiń powyższą sekcję. Oczywiście po dodaniu powyższego fragmentu `project.json` kodu do pliku należy dodać statyczny punkt wejścia. Wraz z odejściem od DNX, usługi DI, które dostarczył, nie są już `static void Main()`dostępne, a zatem musi to być podstawowy punkt wejścia .NET: .

Jeśli masz sekcję "polecenia" w `project.json`swoim , możesz ją usunąć. Niektóre polecenia, które istniały jako polecenia DNU, takie jak polecenia cli struktury jednostek, są przewiowane jako rozszerzenia dla poleceń wiersza polecenia dla poleceń wiersza polecenia. Jeśli stworzyno własne polecenia, które są przy użyciu w projektach, należy zastąpić je rozszerzeniami cli. W takim przypadku `commands` węzeł `project.json` w musi zostać `tools` zastąpiony przez węzeł i musi wymienić zależności narzędzi.

Po wykonaniu tych czynności musisz zdecydować, jaki rodzaj przenośności chcesz dla Ciebie aplikacji. Dzięki programowi .NET Core zainwestowaliśmy w zapewnienie widma opcji przenoszenia, z których możesz wybierać. Na przykład może chcesz mieć w pełni *przenośną* aplikację lub może chcesz mieć *niezależną* aplikację. Opcja aplikacji przenośnej jest bardziej jak .NET Framework aplikacje działają: potrzebuje współużytkowany składnik, aby wykonać go na komputerze docelowym (.NET Core). Niezależna aplikacja nie wymaga zainstalowania programu .NET Core na obiektdocelowy, ale należy utworzyć jedną aplikację dla każdego systemu operacyjnego, który ma być obsługiwany. Te typy przenośności i inne są omówione w dokumencie [typu przenoszenia aplikacji.](../deploying/index.md)

Po nawołaniu, jaki typ przenośności chcesz, należy zmienić docelowe struktury.Once you make a call on what type of portability you want, you need to change your targeted framework(s). Jeśli pisałeś aplikacje dla .NET Core, `dnxcore50` najprawdopodobniej używasz jako docelowej struktury. Z CLI i zmiany, które wprowadził nowy [standard .NET,](../../standard/net-standard.md) framework musi być jednym z następujących:

1. `netcoreapp1.0`- jeśli piszesz aplikacje na .NET Core (w tym ASP.NET aplikacje core)
2. `netstandard1.6`- jeśli piszesz biblioteki klas dla .NET Core

Jeśli używasz innych `dnx` celów, `dnx451` jak trzeba będzie zmienić te, jak również. `dnx451`należy zmienić `net451`na .
Więcej informacji można znaleźć w temacie [standardu .NET.](../../standard/net-standard.md)

Twój `project.json` jest teraz w większości gotowy. Musisz przejść przez listę zależności i zaktualizować zależności do ich nowszych wersji, zwłaszcza jeśli używasz ASP.NET zależności rdzenia. Jeśli używasz oddzielnych pakietów dla interfejsów API BCL, można użyć pakietu czasu uruchomieniowego, jak wyjaśniono w dokumencie [typu przenośności aplikacji.](../deploying/index.md)

Gdy wszystko będzie gotowe, możesz `dotnet restore` spróbować przywrócić[(patrz uwaga).](#dotnet-restore-note) W zależności od wersji zależności może wystąpić błędy, jeśli NuGet nie można rozwiązać zależności dla jednej z platform docelowych powyżej. Jest to problem "point-in-time"; w miarę upływu czasu coraz więcej pakietów będzie obejmować obsługę tych struktur. Na razie jeśli uruchomisz w tym, można użyć `imports` instrukcji w `framework` węźle, aby określić NuGet, że można przywrócić pakiety przeznaczone dla struktury w ramach "importuje" instrukcji.
Błędy przywracania, które otrzymasz w tym przypadku, powinny dostarczyć wystarczających informacji, aby poinformować, które struktury należy zaimportować. Jeśli jesteś lekko zagubiony lub nowy w `dnxcore50` tym, ogólnie rzecz biorąc, określenie i `portable-net45+win8` w `imports` instrukcji należy załatwić sprawę. Poniższy fragment JSON pokazuje, jak to wygląda:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Uruchamianie `dotnet build` pokaże wszelkie ewentualne błędy kompilacji, choć nie powinno być ich zbyt wiele. Po kod jest budowanie i działa prawidłowo, można przetestować go z biegacza. Wykonaj `dotnet <path-to-your-assembly>` i zobacz, jak działa.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
