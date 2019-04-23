---
title: Migrowanie ze środowiska DNX i .NET Core interfejsu wiersza polecenia
description: Migrację, za pomocą środowiska DNX, narzędzia do narzędzia wiersza polecenia platformy .NET Core.
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: 0f00ee6c05a47d976028c3cd4eade2b2b399260b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160839"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrowanie ze środowiska DNX i .NET Core interfejsu wiersza polecenia (project.json)

## <a name="overview"></a>Omówienie
Wersja RC1 platformy .NET Core i ASP.NET Core 1.0 wprowadzono narzędzi środowiska DNX. RC2 wersję platformy .NET Core i ASP.NET Core 1.0 przeniesione ze środowiska DNX dla interfejsu wiersza polecenia platformy .NET Core.

Jako nieznaczne odświeżacz przypomnijmy się, środowiska DNX miała zamiar. Środowiska DNX była środowisko uruchomieniowe i zestaw narzędzi umożliwiających tworzenie platformy .NET Core i dokładniej mówiąc, aplikacje programu ASP.NET Core 1.0. Składa się z 3 części głównej:

1. DNVM — skrypt instalacji uzyskiwania środowiska DNX
2. Środowiska DNX (środowisko uruchomieniowe wykonywania Dotnet -) środowiska uruchomieniowego, które wykonuje kod
3. DNU (Dotnet dewelopera narzędzie) — narzędzia do zarządzania zależnościami, tworzenie i publikowanie własnych aplikacji

Wraz z wprowadzeniem interfejsu wiersza polecenia wszystkie powyższe są teraz częścią jednego zestawu narzędzi. Jednak ponieważ środowiska DNX była dostępna w wersji RC1 przedział czasu, Niewykluczone, że projekty, które zostały utworzone przy użyciu, chcesz opuścić nowych narzędzi interfejsu wiersza polecenia.

W przewodniku migracji opisano podstawowe informacje na temat migrowania projektów zniżki w stosunku do środowiska DNX, a także do wiersza polecenia platformy .NET Core. Jeśli projekt jest uruchamiany tylko na platformie .NET Core, od podstaw, można pominąć za darmo w tym dokumencie.

## <a name="main-changes-in-the-tooling"></a>Główne zmiany w narzędzi
Istnieją pewne ogólne zmiany w narzędzia, które powinny być opisane najpierw.

### <a name="no-more-dnvm"></a>Nie DNVM więcej
DNVM skrót *Menedżera wersji platformy DotNet* był skrypt powłoki bash/programu PowerShell umożliwia zainstalowanie środowiska DNX na swojej maszynie. Dzięki tej współpracy użytkownikom uzyskać środowiska DNX one od źródła danych, które są określone (lub domyślne), a także oznaczania niektórych środowiska DNX, "active", który go umieścić na $PATH dla danej sesji. Umożliwi to za pomocą różnych narzędzi.

DNVM została zakończona, ponieważ jej zestaw funkcji wykonał nadmiarowe zmiany wprowadzone w narzędzi interfejsu wiersza polecenia platformy .NET Core.

Narzędzia interfejsu wiersza polecenia pochodzić uporządkowanej dwa sposoby:

1. Natywnych instalatorów dla danej platformy
2. Skrypt instalacji dla innych sytuacjach (np. serwerów ciągłej integracji)

Biorąc pod uwagę to, funkcje instalacji DNVM nie są potrzebne. Ale co o funkcjach Wybieranie środowiska uruchomieniowego?

Możesz odwoływać się do środowiska uruchomieniowego w swojej `project.json` przez dodanie niektórych wersji pakietu do zależności. Dzięki tej zmianie aplikacji będzie można za pomocą nowego środowiska uruchomieniowego. Te usługi bits na komputerze jest taka sama, jak za pomocą interfejsu wiersza polecenia: Instalowanie środowiska uruchomieniowego przy użyciu jednej z natywnych instalatorów obsługuje lub za pośrednictwem jego skryptu instalacji.

### <a name="different-commands"></a>Różne polecenia
Jeśli używano środowiska DNX użyto niektórych poleceń z jednego z jego trzy części (środowiska DNX, DNU lub DNVM). Za pomocą interfejsu wiersza polecenia zmienić się niektóre z tych poleceń, niektóre z nich są dostępne i niektóre są takie same, ale mają nieco innej semantyki.

Poniższa tabela zawiera mapowanie między poleceń środowiska DNX/DNU i ich odpowiedniki interfejsu wiersza polecenia.

| Polecenie środowiska DNX                    | Polecenia interfejsu wiersza polecenia    | Opis                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| Uruchamianie środowiska DNX                        | Uruchom polecenia DotNet     | Uruchom kod ze źródła.                                                                                           |
| dnu kompilacji                      | Kompilacja DotNet   | Tworzenie pliku IL binarnego kodu.                                                                                |
| Pakiet dnu                       | pakietu DotNet    | Spakować pakietu NuGet kodu.                                                                        |
| środowiska DNX \[polecenia] (na przykład "środowiska dnx sieci web") | N/D\*          | W świecie środowiska DNX Uruchom polecenie zgodnie z definicją w pliku project.json.                                                     |
| Zainstaluj dnu                    | N/D\*          | W świecie środowiska DNX należy zainstalować pakiet jako zależność.                                                            |
| Przywracanie dnu                    | DotNet restore | Przywracanie zależności określone w Twojego pliku project.json. ([patrz Uwaga](#dotnet-restore-note))                                                            |
| Publikowanie dnu                    | Publikowanie DotNet | Publikowanie aplikacji na potrzeby wdrażania w jednej z trzech Form (przenośne, przenośne przy użyciu autonomicznego i urządzeń z natywnym). |
| Zawijanie dnu                       | N/D\*          | W świecie środowiska DNX zawiń project.json w pliku csproj.                                                                    |
| polecenia dnu                   | N/D\*          | W świecie środowiska DNX zarządzać polecenia zainstalowanych globalnie.                                                           |

(\*) — te funkcje nie są obsługiwane w interfejsie wiersza polecenia platformy zgodnie z projektem.

## <a name="dnx-features-that-are-not-supported"></a>Funkcje środowiska DNX, które nie są obsługiwane
Jako tabela powyżej przedstawiono ma funkcji ze świata środowiska DNX, podjęliśmy decyzję o nie obsługują w interfejsie wiersza polecenia, przynajmniej obecnie. W tej sekcji spowoduje przechodzą przez najważniejsze i opisują uzasadnieniem nie obsługuje je, a także rozwiązania problemu, jeśli jest to potrzebne.

### <a name="global-commands"></a>Polecenia globalne
DNU dołączone do koncepcji o nazwie "globalne polecenia". Zostały one zasadniczo aplikacji konsoli postać pakietów NuGet za pomocą skryptu powłoki, który powodowałoby wywołanie pliku wykonywalnego środowiska DNX, określone do uruchomienia aplikacji.

Interfejs wiersza polecenia nie obsługuje tę koncepcję. Jednak obsługuje ona koncepcji dodanie poleceń dla projektu, które może być wywoływany przy użyciu znanej `dotnet <command>` składni.

### <a name="installing-dependencies"></a>Instalacja zależności
Począwszy od wersji 1, nie masz narzędzi interfejsu wiersza polecenia platformy .NET Core `install` polecenia dotyczące instalowania zależności. Aby można było zainstalować pakiet z pakietów NuGet, należy dodać je jako zależność do Twojej `project.json` pliku, a następnie uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)).

### <a name="running-your-code"></a>Uruchamianie kodu
Istnieją dwa główne sposoby, aby uruchomić kod. Jest jednym ze źródła przy użyciu `dotnet run`. W odróżnieniu od `dnx run`, to nie będzie żadnych kompilacji w pamięci. Rzeczywiście wywoła `dotnet build` do kompilowania kodu, a następnie uruchom skompilowany plik binarny.

Innym sposobem jest przy użyciu `dotnet` do uruchomienia kodu. Jest to zrobić, podając ścieżkę do zestawu: `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migracja projektu środowiska DNX interfejsu wiersza polecenia platformy .NET Core
Oprócz używania nowych poleceń podczas pracy z kodem, istnieją trzy główne czynności left migracji ze środowiska DNX:

1. Migrowanie `global.json` plik, jeśli użytkownik ma mieć możliwość użycia interfejsu wiersza polecenia.
2. Migrowanie pliku projektu (`project.json`) do narzędzi interfejsu wiersza polecenia.
3. Migrowanie zniżki w stosunku do dowolnych interfejsów API środowiska DNX, aby ich odpowiedniki BCL.

### <a name="changing-the-globaljson-file"></a>Zmiana plik global.json
`global.json` Pliku działa jak plik rozwiązania w wersji RC1 i RC2 (lub nowszym) projektów. Aby interfejs wiersza polecenia narzędzia (a także programu Visual Studio) do rozróżnienia między RC1 i nowszych wersjach, używają `"sdk": { "version" }` właściwość, o której projekt jest RC1 lub nowszej. Jeśli `global.json` nie ma tego węzła, to zakłada się najnowsze informacje.

Aby można było zaktualizować `global.json` pliku albo usuń właściwość lub ustaw go na wersję narzędzia, które mają być używane w tym przypadku **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrowanie pliku projektu

Interfejs wiersza polecenia i środowiska DNX, użyj tego samego systemu podstawowego projektu, na podstawie `project.json` pliku. Składnia i semantyka pliku projektu są właściwie takie same, z niewielkie różnice w oparciu o scenariusze. Istnieją również pewne zmiany schematu, którą można zobaczyć w [pliku schematu](http://json.schemastore.org/project).

Jeśli tworzysz aplikację konsolową w języku, należy dodać poniższy fragment kodu do pliku projektu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

To powoduje, że `dotnet build` do emitowania punkt wejścia dla aplikacji, efektywnie dzięki czemu kod możliwy do uruchomienia. Jeśli tworzysz bibliotekę klas, po prostu pominąć powyższej sekcji. Oczywiście raz Dodaj powyżej fragment kodu do Twojej `project.json` pliku, należy dodać punktu wejścia statyczne. Wraz z przejściem off środowiska DNX DI usług go nie są już dostępne i dlatego musi to być podstawowy punkt wejścia dla platformy .NET: `static void Main()`.

Jeśli w sekcji "polecenia" Twoje `project.json`, możesz go usunąć. Niektóre polecenia, które są używane do istnieje jako DNU poleceń, takich jak polecenia interfejsu wiersza polecenia programu Entity Framework, są jest przenoszone jako dla projektu rozszerzenia dla interfejsu wiersza polecenia. Jeśli utworzono własne polecenia, które są używane w projektach, należy zastąpić je za pomocą rozszerzeń interfejsu wiersza polecenia. W tym przypadku `commands` w węźle `project.json` musi zostać zastąpiona `tools` węzła i jego potrzebuje informacji o zależności narzędzia.

Po te elementy są gotowe, musisz zdecydować, jakiego typu przenośność chcesz przez aplikację. Za pomocą programu .NET Core mają skupiliśmy do ujawnienia liczne opcje przenoszenia, które można wybierać. Na przykład możesz chcieć mieć pełni *przenośne* aplikacji lub możesz chcieć mieć *niezależna* aplikacji. Opcja przenośnym aplikacja jest bardziej jak działanie aplikacji .NET Framework: potrzebny, aby współużytkowanego składnika, aby uruchomić go na komputerze docelowym (.NET Core). Samodzielna aplikacja nie wymaga platformy .NET Core do zainstalowania w elemencie docelowym, ale należy utworzyć jedną aplikację dla każdego systemu operacyjnego, chcesz obsługiwać. Te typy przenośność i inne, które zostały omówione w [Typ przenoszenia aplikacji](../deploying/index.md) dokumentu.

Po wprowadzeniu wywołanie w jakiego rodzaju przenośność ma musisz zmienić swoje framework(s) docelowych. Podczas pisania aplikacji dla platformy .NET Core, najprawdopodobniej używano wcześniej `dnxcore50` jako swojej platformy docelowej. Za pomocą interfejsu wiersza polecenia i zmiany, nowe [.NET Standard](../../standard/net-standard.md) dostosowane, struktura musi być jedną z następujących czynności:

1. `netcoreapp1.0` -Jeśli piszesz aplikacje na platformie .NET Core (w tym aplikacje platformy ASP.NET Core)
2. `netstandard1.6` -Jeśli piszesz bibliotek klas dla platformy .NET Core

Jeśli używasz innych `dnx` jest przeznaczony dla, takie jak `dnx451` , musisz również zmienić te. `dnx451` należy je zmienić `net451`.
Zapoznaj się [.NET Standard](../../standard/net-standard.md) tematu, aby uzyskać więcej informacji.

Twoje `project.json` przede wszystkim jest gotowy. Musisz przejść przez listy zależności i zaktualizuj zależności do ich nowszych wersji, zwłaszcza, jeśli używasz zależności platformy ASP.NET Core. Jeśli były używane oddzielne pakiety dla interfejsów API BCL, można użyć od pakietu środowiska uruchomieniowego, jak wyjaśniono w [Typ przenoszenia aplikacji](../deploying/index.md) dokumentu.

Gdy wszystko będzie gotowe, możesz spróbować przywrócenie za pomocą `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)). W zależności od wersji zależności mogą wystąpić błędy, jeśli NuGet nie może rozpoznać zależności dla jednej z powyższych struktury docelowej. Jest to problem "punktu w czasie"; w miarę postępów czasu coraz więcej pakietów będzie obejmują wsparcie dla tych platform. Teraz, jeśli napotkasz ten, możesz użyć `imports` instrukcji wewnątrz `framework` węzła w celu określenia NuGet, przywrócić pakiety przeznaczanie wewnątrz instrukcji "imports".
Przywracanie błędów, które otrzymujesz w tym przypadku powinna zawierać informacje wystarczające do poinformować Cię, które struktur potrzebne do zaimportowania. Ogólnie rzecz biorąc, określenie przypadku nieco utracone lub jesteś nowym użytkownikiem to `dnxcore50` i `portable-net45+win8` w `imports` instrukcji należy wykonać lewy. Poniższy fragment kodu JSON pokazuje, jak to wygląda:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Uruchamianie `dotnet build` będą wyświetlane ewentualne błędy kompilacji ostatecznej, chociaż nie powinny istnieć zbyt wiele z nich. Po kodzie buduje i działa poprawnie, możesz ją przetestować przy użyciu modułu uruchamiającego. Wykonaj `dotnet <path-to-your-assembly>` i zobaczyć ją uruchomić.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
