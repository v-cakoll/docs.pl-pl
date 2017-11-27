---
title: Migrowanie z DNX do platformy .NET Core interfejsu wiersza polecenia
description: "Migracja z przy użyciu środowiska DNX narzędzi do narzędzi interfejsu wiersza polecenia platformy .NET Core."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: c0d70120-78c8-4d26-bb3c-801f42fc2366
ms.openlocfilehash: 1e2ab018fc690b31b59a04bf8c0c0990225c293b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrowanie z DNX do platformy .NET Core interfejsu wiersza polecenia (project.json)

## <a name="overview"></a>Omówienie
Wersja RC1 .NET Core i ASP.NET Core 1.0 wprowadzono DNX narzędzi. Wersja RC2 .NET Core i ASP.NET Core w wersji 1.0 są przenoszone z DNX na .NET Core interfejsu wiersza polecenia.

Jako nieznaczne odświeżacz umożliwia recap DNX wynosiła około. DNX był środowisko wykonawcze i zestawu narzędzi użytą do skompilowania .NET Core i, w szczególności aplikacje platformy ASP.NET Core 1.0. Składa się z 3 części głównej:

1. DNVM - skrypt instalacji skryptu do uzyskania DNX
2. Środowiska DNX (Dotnet wykonywania Runtime) — środowisko uruchomieniowe, które wykonuje kodu
3. DNU (Dotnet dewelopera narzędzie) — narzędzia do zarządzania zależności, tworzenie i publikowanie aplikacji

Korzystając z interfejsu wiersza polecenia wszystkie powyższe są teraz częścią jednego zestawu narzędzi. Jednak ponieważ DNX była dostępna w przedziale czasu RC1, może być projektów, które zostały utworzone przy użyciu którego chcesz opuścić do nowych narzędzi interfejsu wiersza polecenia. 

Ten przewodnik migracji obejmuje podstawowe informacje dotyczące sposobu przeprowadzenia migracji projekty znajdujące się na nich DNX i na .NET Core interfejsu wiersza polecenia. Jeśli projekt jest uruchamiany tylko na .NET Core, od początku, za darmo można pominąć ten dokument. 

## <a name="main-changes-in-the-tooling"></a>Główne zmiany w narzędzi
Istnieją pewne ogólne zmiany w narzędzia, należy najpierw przedstawiono. 

### <a name="no-more-dnvm"></a>Nie więcej DNVM
DNVM skrót *Menedżer wersji DotNet* został użyty do zainstalowania na komputerze środowiska DNX skryptu bash PowerShell. Jego udzielenie pomocy użytkownikom DNX one z określone źródło (lub domyślne), a także oznaczyć niektórych środowiska DNX "active", który przełączyć go w $PATH dla danej sesji. Umożliwi to użycie różnych narzędzi.

DNVM została zakończona, ponieważ jej zestaw funkcji wykonał nadmiarowe zmiany przychodzących narzędzi interfejsu wiersza polecenia platformy .NET Core.

Narzędzi interfejsu wiersza polecenia są pakowane przede wszystkim na dwa sposoby:

1. Instalatorzy macierzystego dla danej platformy
2. Skrypt instalacji dla innych sytuacjach (np. serwerów CI)

Biorąc pod uwagę to, DNVM install funkcje nie są wymagane. Co funkcji środowiska uruchomieniowego wybór jednak? 

Możesz odwoływać się do środowiska wykonawczego w Twojej `project.json` dodając określoną wersję pakietu zależności. Dzięki tej zmianie aplikacji będzie mógł używać nowego środowiska uruchomieniowego usługi bits. Pobieranie te usługi bits na komputerze jest taka sama, jak w przypadku interfejsu wiersza polecenia: zainstaluj środowisko uruchomieniowe przy użyciu jednej z natywnego instalatorów obsługuje lub za pośrednictwem jego skrypt instalacji. 

### <a name="different-commands"></a>Inne polecenia
Jeśli były używane DNX, używane niektóre polecenia z jednego z jego trzech części (DNX, DNU lub DNVM). Z poziomu interfejsu wiersza polecenia zmiana niektórych z tych poleceń, niektóre nie są dostępne i niektóre są takie same, ale ma nieco inne semantyki. 

W poniższej tabeli przedstawiono mapowanie między polecenia DNX/DNU i ich odpowiedniki interfejsu wiersza polecenia.


| Polecenie DNX                       | Polecenia interfejsu wiersza polecenia       | Opis                                                                                                       |
|--------------------------------   |----------------   |-----------------------------------------------------------------------------------------------------------------  |
| Uruchom DNX                           | Uruchom DotNet        | Uruchomienie kodu ze źródła.                                                                                             |
| dnu kompilacji                         | Kompilacja DotNet      | Tworzenie pliku binarnego IL kodu.                                                                                  |
| Pakiet dnu                          | Pakiet DotNet       | Spakować pakietu NuGet kodu.                                                                          |
| DNX \[polecenia] (na przykład "web dnx")   | N/D\*             | W świecie DNX Uruchom polecenie zgodnie z definicją w pliku project.json.                                                       |
| Instalacja dnu                       | N/D\*             | W świecie DNX należy zainstalować pakiet jako zależność.                                                              |
| Przywracanie dnu                       | Przywracanie DotNet    | Przywróć zależności określone w pliku project.json. ([patrz Uwaga](#dotnet-restore-note))                                                               |
| Publikowanie dnu                       | Publikowanie DotNet    | Publikowanie aplikacji w celu wdrożenia w jednym z trzech formularzy (przenośny, przenośne z macierzystego i autonomiczne).    |
| Zawijaj dnu                          | N/D\*             | W świecie DNX zawijanie project.json w csproj.                                                                      |
| polecenia dnu                      | N/D\*             | W świecie DNX Zarządzanie globalnie zainstalowanej poleceń.                                                             |

(\*) — te funkcje nie są obsługiwane w interfejsu wiersza polecenia zgodnie z projektem. 

## <a name="dnx-features-that-are-not-supported"></a>Funkcje środowiska DNX, które nie są obsługiwane
Jako tabeli powyżej przedstawiono są funkcje ze świata DNX, który zdecydowaliśmy się na brak obsługi w interfejsu wiersza polecenia, co najmniej w chwili obecnej. W tej sekcji zostanie przejść przez najważniejsze alerty i przedstawiają uzasadnienie nie obsługuje je, a także rozwiązania problemu, jeśli jest to potrzebne.

### <a name="global-commands"></a>Polecenia globalne
DNU pochodzi z pojęcie o nazwie "polecenia globalne". Zostały one zasadniczo aplikacji konsoli dostarczana w w pakiety NuGet za pomocą skryptu powłoki, które może wywołać DNX określone do uruchomienia aplikacji. 

Interfejsu wiersza polecenia nie obsługuje tę koncepcję. Obsługuje jednak pojęcie Dodawanie poleceń dla projektu, które mogą być wywoływane przy użyciu znanych `dotnet <command>` składni.

### <a name="installing-dependencies"></a>Instalacja zależności
Począwszy od wersji 1, nie ma narzędzi interfejsu wiersza polecenia platformy .NET Core `install` polecenia dotyczące instalowania zależności. Aby można było zainstalować pakiet z pakietu NuGet, należy dodać ją jako zależność do Twojej `project.json` pliku, a następnie uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)). 

### <a name="running-your-code"></a>Wykonywanie kodu użytkownika
Istnieją dwa sposoby uruchamiania kodu. Jest jednym ze źródła, z `dotnet run`. W odróżnieniu od `dnx run`, nie będzie wykonywał żadnych kompilacji w pamięci. Rzeczywiście wywoła `dotnet build` do kompilacji kodu, a następnie uruchom plik binarny wbudowanych. 

Innym sposobem jest przy użyciu `dotnet` do uruchomienia kodu. Jest to zrobić, podając ścieżkę do używanego zestawu: `dotnet path/to/an/assembly.dll`. 

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrowanie projektu DNX do .NET Core interfejsu wiersza polecenia
Oprócz przy użyciu nowych poleceń podczas pracy z kodu, istnieją trzy główne czynności migracji ze środowiska DNX w lewo:

1. Migrowanie `global.json` plik, jeśli użytkownik ma mieć możliwość korzystania z interfejsu wiersza polecenia.
2. Migracji pliku projektu (`project.json`) do narzędzi interfejsu wiersza polecenia.
3. Migrowanie wylogowuje wszystkie interfejsy API środowiska DNX w celu ich odpowiedniki BCL. 

### <a name="changing-the-globaljson-file"></a>Zmienianie pliku global.json
`global.json` Plików działa jak plik rozwiązania RC1 i RC2 (lub nowsza) projektów. Aby interfejsu wiersza polecenia narzędzia (a także Visual Studio) w celu rozróżnienia RC1 i nowszych wersjach, używają `"sdk": { "version" }` właściwość o który projekt jest RC1 lub nowszym. Jeśli `global.json` nie ma tego węzła, jest przyjmowana r. 

Aby można było zaktualizować `global.json` pliku, Usuń właściwość lub ustaw ją na dokładnej wersji narzędzia, które mają być używane w tym przypadku **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migracji pliku projektu
Interfejsu wiersza polecenia i DNX używa tego samego systemu podstawowego projektu, na podstawie `project.json` pliku. Składnia i semantyka pliku projektu są bardzo dużo takie same, z niewielkie różnice w oparciu scenariusze. Istnieją również pewne zmiany do schematu, który można wyświetlić w [pliku schematu](http://json.schemastore.org/project).

Jeśli tworzysz aplikację konsoli, należy dodać następujący fragment kodu w pliku projektu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

To powoduje, że `dotnet build` można wyemitować punkt wejścia dla aplikacji, efektywnie wprowadzania kodu do uruchomienia. Jeśli tworzysz biblioteki klas, po prostu pominąć powyższej sekcji. Oczywiście raz Dodaj powyżej fragment do Twojej `project.json` pliku, należy dodać punkt wejścia statycznych. Wraz z przejściem poza DNX Podpisane usług go nie będą już dostępne i w związku z tym musi to być podstawowy punkt wejścia .NET: `static void Main()`.

Jeśli w sekcji "polecenia" Twojej `project.json`, można go usunąć. Są niektórych poleceń, które umożliwiają istnieje jako DNU poleceń, takich jak polecenia interfejsu wiersza polecenia Entity Framework, są przenoszone do można rozszerzeń dla projektu interfejsu wiersza polecenia. Jeśli utworzono własne polecenia, które są używane w projektach, należy zastąpić rozszerzeń interfejsu wiersza polecenia. W takim przypadku `commands` w węźle `project.json` musi zostać zastąpiona `tools` węzła i jego potrzebuje o zależności narzędzia. 

Po zakończeniu tych czynności, musisz zdecydować, jakiego typu przenośność mają przez aplikację. Z platformą .NET Core skupiliśmy mają do udostępnia szeroką gamę opcji przenośność, które są dostępne. Na przykład można mieć pełni *przenośne* aplikacji lub może być *niezależne* aplikacji. Opcja przenośnych aplikacji jest bardziej przypominają pracy aplikacji .NET Framework: wymaga składnika współużytkowanego do wykonania go na komputerze docelowym (.NET Core). Aplikację autonomiczną nie wymaga platformy .NET Core do zainstalowania w systemie docelowym, ale trzeba utworzyć jedną aplikację dla każdego systemu operacyjnego do obsługi. Te typy przenośność i inne zostały omówione w [typu przenośność aplikacji](../deploying/index.md) dokumentu. 

Po wprowadzeniu wywołanie w rodzaju przenośność ma musisz zmienić Twojego framework(s) docelowych. Podczas pisania aplikacji dla platformy .NET Core, najprawdopodobniej używania `dnxcore50` jako z docelową platformą. Z poziomu interfejsu wiersza polecenia i zmiany który nowy [.NET Standard](../../standard/net-standard.md) dostosowane, platformę musi być jedną z następujących czynności:

1. `netcoreapp1.0`-podczas pisania aplikacji na .NET Core (w tym aplikacje platformy ASP.NET Core)
2. `netstandard1.6`— Jeśli piszesz biblioteki klas dla platformy .NET Core

Jeśli używane są inne `dnx` elementów docelowych, takie jak `dnx451` należy również zmienić te. `dnx451`należy zmienić `net451`. Zapoznaj się z [.NET Standard](../../standard/net-standard.md) tematu, aby uzyskać więcej informacji. 

Twoje `project.json` przede wszystkim jest gotowy. Należy przeprowadzić liście zależności i zaktualizuj zależności do ich nowszych wersji, zwłaszcza, jeśli używasz platformy ASP.NET Core zależności. Jeśli były używane osobne pakiety dla interfejsów API BCL, można użyć pakietu środowiska uruchomieniowego, zgodnie z objaśnieniem w [typu przenośność aplikacji](../deploying/index.md) dokumentu. 

Gdy wszystko będzie gotowe, możesz spróbować przywrócenie za pomocą `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)). W zależności od wersji zależności mogą wystąpić błędy, jeśli NuGet nie można rozpoznać zależności dla jednego z platformy docelowe powyżej. Jest to problem "punktu w czasie"; w miarę postępów czasu coraz więcej pakietów obejmuje obsługę tych platform. W przypadku teraz, po uruchomieniu w tym celu można użyć `imports` instrukcji wewnątrz `framework` węzeł, aby określić NuGet, czy można przywrócić pakietów przeznaczonych dla framework w instrukcji "imports". Przywracanie błędy, które pojawia się w tym przypadku powinien zawierać informacje wystarczające do ustalenia, które struktur potrzebne do importowania. Jeśli jesteś nieco utracone ani na to, ogólnie rzecz biorąc, określając `dnxcore50` i `portable-net45+win8` w `imports` instrukcji należy wykonać, lewy. Poniższy fragment JSON pokazuje, jak wygląda ona następująco:

```json
    "frameworks": {
        "netcoreapp1.0": { 
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Uruchomiona `dotnet build` wyświetli błędy kompilacji ostateczna, mimo że nie powinny być zbyt wiele z nich. Po kodzie buduje i działa prawidłowo, można przetestować go z modułu uruchamiającego testy. Wykonanie `dotnet <path-to-your-assembly>` i zobaczyć ją uruchomić.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]