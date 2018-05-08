---
title: Przechowywanie wersji platformy .NET core
description: Dowiedz się, jak działa przechowywanie wersji platformy .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: 0cfd620d2b6e6e60531b0e2aa938c1ed64b6af23
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="net-core-versioning"></a>Przechowywanie wersji platformy .NET core

Oprogramowanie .NET core składa się z [pakietów NuGet](../packages.md), narzędzia i platform, które są dystrybuowane jako jednostka. Każdy z tych warstw platformy może być kontrolą wersji oddzielnie, włączanie większą elastyczność. Wprawdzie w tym zakresie jest elastyczność znaczących przechowywania wersji, dostępna jest również chęć wersji platformy jako jednostki, aby ułatwić zrozumienie produktu.

W tym artykule celem jest wyjaśnienie, jak są numerów wersji zestawu SDK programu .NET Core i środowiska uruchomieniowego.

Istnieje wiele części ruchome tej wersji niezależnie w .NET Core. Jednak począwszy od programu .NET Core 2.0 jest łatwy do zrozumienia numer wersji najwyższego poziomu każdy rozumie, aby można *wersji* ".NET Core" jako całość. Pozostała część tego dokumentu przechodzi w stan szczegółowe informacje o wersji tych części. Te informacje mogą być istotne, jeśli jesteś Menedżera pakietów, na przykład.

> [!IMPORTANT]
> Szczegóły versioning wyjaśnione w tym temacie nie dotyczą bieżącej wersji zestawu SDK programu .NET Core i środowiska uruchomieniowego.
> Wersja schematu zmienia w przyszłych wersjach. Zostanie wyświetlony w bieżącej propozycji [dotnet/projektów](https://github.com/dotnet/designs/pull/29) repozytorium.

## <a name="versioning-details"></a>Przechowywanie wersji szczegóły

.NET Core 2.0 pliki do pobrania Pokaż numeru wersji pojedynczego w nazwach plików. Ujednolicone zostały następujące numery wersji:

* Udostępniony framework i skojarzone środowiska uruchomieniowego.
* .NET Core SDK i interfejsu wiersza polecenia skojarzony .NET Core.
* `Microsoft.NETCore.App` Metapackage.

Użycie jednej wersji numer sprawia, że ułatwia użytkownikom odnalezienie jakiej wersji zestawu SDK do zainstalowania na komputerach deweloperów i jakie odpowiednią wersję platformy udostępniony powinien być gdy czas do udostępnienia do środowiska produkcyjnego. Podczas pobierania zestawu SDK lub środowisko uruchomieniowe, numer wersji, który zostanie wyświetlony ma być takie same.

### <a name="installers"></a>Pliki instalacyjne

.NET Core 2.0, pliki do pobrania dla [codziennie kompilacje](https://github.com/dotnet/core-setup#daily-builds) i [zwalnia](https://www.microsoft.com/net/download/core) stosować się do nowego schemat nazewnictwa, która ułatwia zrozumienie.
Instalator interfejsu użytkownika w tych plikach do pobrania została zmodyfikowana również wyraźnie przedstawić nazwy i wersje instalowanych składników. W szczególności tytułów teraz Pokaż numer wersji tego samego znajduje się w nazwie pliku pobierania.

#### <a name="file-name-format"></a>Format nazwy pliku

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Oto kilka przykładów tego formatu:

```
dotnet-runtime-2.0.4-macos.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win10-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-fedora.24-x64.tar.gz               # Fedora 24 binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb              # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb           # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb               # SDK tools
```

Format jest możliwy do odczytu i jasno wskazuje czego pobieranie wersji jest i gdzie można go użyć. Nazwa pakietu środowiska uruchomieniowego zawiera `runtime`, i zestaw SDK zawiera `SDK`.

#### <a name="ui-string-format"></a>Format ciągu interfejsu użytkownika

Wszystkie opisy witryny sieci web i ciągi interfejsu użytkownika w instalatorów pozostają spójne, dokładne i proste. W poniższej tabeli przedstawiono kilka przykładów:

| Instalator | Tytuł okna                          | Inną zawartość w Instalatorze | Co to jest zainstalowany                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | Instalator programu .NET core 2.0 SDK (x 64)     | Oprogramowanie .NET core 2.0.4 zestawu SDK        | .NET Core 2.0.4 Tools + .NET Core 2.0.4 Runtime |
| Środowisko uruchomieniowe   | Środowisko uruchomieniowe (x64) Instalatora programu .NET core 2.0 | .NET Core 2.0.4 Runtime    | .NET Core 2.0.4 Runtime                         |

Wersje zapoznawcze różnią się tylko nieznacznie:

| Instalator | Tytuł okna                                    | Inną zawartość w Instalatorze        | Co to jest zainstalowany                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | Instalatora programu .NET core 2.0 wersja zapoznawcza 1 SDK (x 64)     | 1 — zestaw SDK platformy .NET core 2.0.0 w wersji Preview     | Narzędzia programu .NET core 2.0.0 Preview 1 + .NET Core 2.0.0 Preview 1 środowiska wykonawczego |
| Środowisko uruchomieniowe   | Instalatora programu .NET core 2.0 wersja zapoznawcza 1 (x64) środowiska wykonawczego | Środowisko uruchomieniowe platformy .NET core 2.0.0 Preview 1 | Środowisko uruchomieniowe platformy .NET core 2.0.0 Preview 1                                   |

Może się zdarzyć, że wersja zestawu SDK zawiera więcej niż jedną wersję środowiska uruchomieniowego. W takim przypadku Instalator UX wygląda następująco (tylko wersja zestawu SDK jest wyświetlany i zainstalowanych wersji środowiska uruchomieniowego są wyświetlane na stronie podsumowania pod koniec procesu instalacji w systemach Windows i Mac):

| Instalator | Tytuł okna                      | Inną zawartość w Instalatorze                                   | Co to jest zainstalowany                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | Instalator programu .NET core 2.1 zestawu SDK (x 64) | .NET Core 2.1.1 SDK <br> .NET Core 2.1.1 Runtime <br> Środowisko uruchomieniowe platformy .NET core 2.0.6 | Narzędzia .NET core 2.1.1 + środowisko uruchomieniowe platformy .NET Core 2.1.1 środowisko uruchomieniowe platformy .NET Core 2.0.6 |

Istnieje również możliwość, że narzędzia .NET Core muszą zostać zaktualizowane, bez zmiany środowiska uruchomieniowego. W takim przypadku zwiększa się wersja zestawu SDK (na przykład, aby 2.1.2), a następnie środowiska uruchomieniowego przechwytuje następnym razem go (na przykład środowiska uruchomieniowego i zestawu SDK wysłać przy następnym jako 2.1.3) jest dostarczany.

### <a name="package-managers"></a>Menedżerowie pakietu

Oprogramowanie .NET core mogą być dystrybuowane przez inne jednostki, niż firmy Microsoft. W szczególności właścicieli dystrybucji systemu Linux i maintainers pakietu może Dodawanie pakietów platformy .NET Core ich menedżerów pakietu. Aby uzyskać zalecenia dotyczące sposobu tych pakietów powinny być nazywane i kontrolą wersji, zobacz [pakowania dystrybucji .NET Core](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Ustaw minimalną pakietu

* `dotnet-runtime-[major].[minor]`: środowiska wykonawczego o określonej wersji (tylko najnowszą wersję poprawki dla danej głównych + pomocnicza kombinacji powinny być dostępne w Menedżera pakietów). Nowe wersje poprawki pakietu, ale nowe wersje pomocnicze lub główne są osobne pakiety.

  **Zależności**: `dotnet-host`

* `dotnet-sdk`: najnowszej wersji zestawu SDK. `update` przedstawia przekazywania głównych i pomocniczych i poprawka wersji.

  **Zależności**: r `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: zestaw SDK o określonej wersji. Określona wersja jest najwyższej wersji dołączone dołączone struktur udostępnionych, tak, aby użytkownicy można łatwo dotyczą zestawu SDK udostępnionego framework. Nowe wersje poprawki pakietu, ale nowe wersje pomocnicze lub główne są osobne pakiety.

  **Zależności**: `dotnet-host`, co najmniej jeden `dotnet-runtime-[major].[minor]` (jedna z tych jest używana przez zestaw SDK kodu, inne są tutaj dla użytkowników skompilować i uruchomić przed).

* `dotnet-host`: najnowsze hosta.

##### <a name="preview-versions"></a>Wersji Preview

Maintainers pakietu może zadecydować o obejmują wersje podglądu środowiska uruchomieniowego i zestawu SDK. Nie dołączaj tych wersji zapoznawczych wycofanie `dotnet-sdk` pakiet, ale można je zwolnić pakiety w wersji ze znacznikiem Podgląd dodatkowe dołączone do wersji głównej i pomocniczej części nazwy. Na przykład mogą istnieć `dotnet-sdk-2.0-preview1-final` pakietu.

### <a name="docker"></a>Docker

Ogólne tag Docker konwencji nazewnictwa jest umieszczenie numeru wersji przed nazwą składnika. Tę Konwencję może nadal być wykorzystywane. Bieżące znaczniki zawierają tylko wersję środowiska uruchomieniowego w następujący sposób.

* 1.0.8-Runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-Runtime
* 2.1.1-sdk

Tagi SDK powinny zostać uaktualnione do reprezentowania wersji zestawu SDK zamiast środowiska wykonawczego.

Istnieje również możliwość, usunięto narzędzi interfejsu wiersza polecenia platformy .NET Core (dołączony do zestawu SDK) ale reship z istniejącego środowiska wykonawczego. W takim przypadku zwiększa się wersja zestawu SDK (na przykład, aby 2.1.2), a następnie środowiska uruchomieniowego przechwytuje następnym razem go (na przykład środowiska uruchomieniowego i zestawu SDK wysłać następującym czasie jako 2.1.3) jest dostarczany.

## <a name="semantic-versioning"></a>Wersjonowania semantycznego

Używa platformy .NET core [Wersjonowania semantycznego (programu SemVer)](http://semver.org/), przyjmowanie stosowania `MAJOR.MINOR.PATCH` versioning stopnia i typ zmiany jest opisywany przy użyciu różnych części numer wersji.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalny `PRERELEASE` i `BUILDNUMBER` części nigdy nie są częścią obsługiwanych wersji i istnieje tylko w przypadku kompilacji co noc, lokalne kompilacje ze źródła obiekty docelowe, i zwalnia nieobsługiwanej wersji zapoznawczej.

### <a name="how-version-numbers-are-incremented"></a>Jak są zwiększane, numery wersji?

`MAJOR` Kiedy jest zwiększany:

- Stara wersja nie jest już obsługiwana.
- Nowszej `MAJOR` przyjęto wersję istniejącego zależności.
- Domyślne ustawienie niedoskonałość zgodności zostanie zmieniona na "off".

`MINOR` Kiedy jest zwiększany:

- Dodawany jest publicznej powierzchni interfejsu API.
- Dodawany jest nowe zachowanie.
- Nowszej `MINOR` przyjęto wersję istniejącego zależności.
- Wprowadzono nowe zależności.

`PATCH` Kiedy jest zwiększany:

- Wprowadzono poprawki błędów.
- Zostanie dodana jego obsługa dla nowszej platformy.
- Nowszej `PATCH` przyjęto wersję istniejącego zależności.
- Inne zmiany nie mieści się jednym z poprzednich przypadków.

W przypadku wielu zmian najwyższy element dotyczy poszczególnych zmian jest zwiększany, a następujące klucze są resetowane do zera. Na przykład, jeśli `MAJOR` jest zwiększany, `MINOR` i `PATCH` jest resetowany do zera. Gdy `MINOR` jest zwiększany, `PATCH` jest resetowany do zera podczas `MAJOR` jest pozostało bez zmian.

### <a name="preview-versions"></a>Wersji Preview

Podgląd wersji `-preview[number]-([build]|"final")` dołączone do wersji. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Obsługa wersji

Po zlecenia trafia, gałęzie, które zlecenia zwykle stop produkujących codziennie kompilacje i zamiast tego uruchomić produkujących obsługi kompilacji. Wersje obsługi mają `-servicing-[number]` dołączone do wersji. Na przykład `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS, a bieżąca

Istnieją dwa pociągu wersji dla platformy .NET Core: długi okres pomocy technicznej (LTS) i bieżący. Który umożliwia użytkownikom wybierz poziom stabilności i nowe funkcje, które mają, podczas nadal obsługiwane.

- LTS oznacza rzadziej pobrać nowe funkcje, ale masz więcej dojrzałe platformy. LTS ma również dłuższy okres pomocy technicznej.
- Bieżąca oznacza częściej pobrać nowe funkcje i interfejsy API, ale wadą jest to, że masz krótszą okno czasu na zainstalowanie aktualizacji i aktualizacje wystąpić częściej. Aktualnie jest także w pełni obsługiwane, ale czas obsługi jest krótszy niż LTS.

Wersja "Bieżący" może pobrać podwyższony do LTS.

"LTS" i "Bieżący" należy traktować jako etykiety, które testujemy na określonymi wersjami, aby oświadczenie o skojarzone poziomu wsparcia.

Aby uzyskać więcej informacji, zobacz [.NET Core obsługi cyklu życia zestawieniem](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Szczegóły systemu kontroli wersji

Oprogramowanie .NET core składa się z następujących części:

- Host: albo *dotnet.exe* dla aplikacji zależnych od framework lub  *\<nazwa_aplikacji > .exe* dla swojej aplikacji.
- Zestaw SDK (zestaw niezbędnych narzędzi na komputerze dewelopera, ale nie w środowisku produkcyjnym).
- Środowisko wykonawcze.
- Implementacja udostępnionego framework dystrybuowanych jako pakietów. Każdy pakiet jest wersjonowany niezależnie, szczególnie w przypadku wersji poprawki.
- Opcjonalnie, zbiór [metapackages](../packages.md) które zawierają odniesienia szczegółowych pakietów jako wersjonowaną jednostkę. Metapackages może mieć określonej wersji niezależnie od pakietów.

Oprogramowanie .NET core zawiera także zestaw docelowych platform (na przykład `netstandard` lub `netcoreapp`) reprezentujące stopniowo większy zestaw interfejsu API, jak są zwiększane numerów wersji.

### <a name="net-standard"></a>.NET standard

.NET standard korzysta `MAJOR.MINOR` schemat przechowywania wersji. `PATCH` poziom nie jest przydatne w przypadku .NET Standard, ponieważ wyraża zestaw umów, które iterowane na rzadziej i nie stanowi te same wymagania dotyczące przechowywania wersji jako rzeczywistego wykonania.

Nie istnieje żadne rzeczywiste sprzężenie wersje .NET Standard i .NET Core: .NET Core 2.0 stanie się implementuje standardowe .NET w wersji 2.0, ale nie ma gwarancji, że w przyszłych wersjach programu .NET Core przypisze do tej samej wersji platformy .NET Standard. Oprogramowanie .NET core mogą być interfejsów API, które nie są zdefiniowane przez .NET Standard i jako taki może nastąpić nowe wersje bez konieczności nowe standardowe .NET. .NET standard jest również pojęcie ma zastosowanie do innych celów, takich jak .NET Framework lub Mono, nawet jeśli jego powstania stało się pokrywa się z tym oprogramowanie .NET Core.

### <a name="packages"></a>Pakiety

Pakiety bibliotekę rozwijać i wersji niezależnie. Pakiety, które nakładają się przy użyciu systemu .NET Framework. \* zestawy zazwyczaj używają wersji 4.x, dopasowanie się do przechowywania .NET Framework 4.x wersji (wybór historycznych). Pakiety, które nie nakładają się z bibliotekami .NET Framework (na przykład [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) zazwyczaj są liczone od 1.0 i zwiększyć stamtąd.

Pakiety opisanego przez [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) są traktowane specjalnie z powodu w podstawowej platformy.

`NETStandard.Library` pakiety zostaną zwykle wersji jako zestaw, ponieważ mają one poziomie implementacji zależności między nimi.

### <a name="metapackages"></a>Metapackages

Przechowywanie wersji dla platformy .NET Core metapackages zależy od wersji platformy .NET Core, które są częścią.

Na przykład metapackages w .NET Core 2.1.3 powinien wszystkie mają 2.1 jako ich `MAJOR` i `MINOR` numerów wersji.

Wersja poprawki dla metapackage jest zwiększany za każdym razem, gdy są aktualizowane wszystkie pakiety, do którego istnieje odwołanie. Poprawka nie zawierają zaktualizowane framework w wersji. W związku z tym metapackages nie są ściśle zgodne programu SemVer ponieważ ich schemat przechowywania wersji nie reprezentuje stopnia zmiany w podstawowym pakietów, ale głównie z poziomu interfejsu API.

Obecnie nie istnieją dwa podstawowe metapackages dla platformy .NET Core:

**Microsoft.NETCore.App**

- w wersji 1.0 lub nowszym .NET Core 1.0 (te wersje są zgodne).
- Mapuje `netcoreapp` framework.
- Opisuje pakiety w dystrybucji .NET Core.

Uwaga: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) jest inny metapackage .NET Core, która istnieje na zgodność ze standardowej implementacji .NET wstępne platformy .NET. Go nie mapowania na określonej platformy, więc jego wersje, takich jak pakiet.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) w tym artykule opisano bibliotek, które są częścią [.NET Standard](../../standard/library.md). Dotyczy wszystkich implementacji .NET, które obsługują .NET Standard, takich jak .NET Framework, .NET Core i Mono.

### <a name="target-frameworks"></a>Docelowych platform

TARGET framework w wersji zostały zaktualizowane po dodaniu nowych interfejsów API. Mają one nie zawierają wersji poprawki, ponieważ stanowią one kształtu interfejsu API i nie dotyczy implementacji. Wersje główne i pomocnicze jest zgodny z regułami programu SemVer określony wcześniej i pokrywa się z `MAJOR` i `MINOR` liczby dystrybucje .NET Core ich wdrażania.

## <a name="versioning-in-practice"></a>Przechowywanie wersji w praktyce

Po pobraniu .NET Core nazwa pobranego pliku niesie wersji, na przykład `dotnet-sdk-2.0.4-win10-x64.exe`.

Brak zatwierdzeń i żądań ściągnięcia na repozytoriów .NET Core w serwisie GitHub codziennie, co nowego w tworzy wiele bibliotek. Nie jest praktyczne do tworzenia nowych wersji publicznej platformy .NET Core dla każdej zmiany. Zamiast tego zmiany są agregowane przez nieokreślony czas (na przykład, tygodnie lub miesiące) przed wprowadzeniem nowych publicznego stabilną wersję platformy .NET Core.

Nowa wersja programu .NET Core może oznaczać kilka kwestii:

- Nowe wersje pakietów i metapackages.
- Nowe wersje różnych platform, zakładając, że dodanie nowych interfejsów API.
- Nowa wersja dystrybucji .NET Core.

### <a name="shipping-a-patch-release"></a>Wysyłanie zlecenia poprawki

Po wysyłania wydaniem .NET Core, takich jak wersji 2.0.0, poziom poprawki zmian do bibliotek .NET Core błędów i poprawa wydajności i niezawodności. Oznacza to, że zostały wprowadzone nie nowe interfejsy API. Różne metapackages są aktualizowane w celu odwołania się do zaktualizowanych pakietów biblioteki .NET Core. Kontrolą wersji jako poprawek i aktualizacji są metapackages (`MAJOR.MINOR.PATCH`). Docelowych platform nigdy nie są aktualizowane w ramach wersji poprawki. Nowe dystrybucji .NET Core zwolnieniu z numerem wersji, która odpowiada `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-minor-release"></a>Wysyłanie wersji pomocniczej

Po wysyłania wersji platformy .NET Core z zwiększany `MAJOR` numer wersji, nowe interfejsy API są dodawane do bibliotek .NET Core na potrzeby nowych scenariuszy. Różne metapackages są aktualizowane w celu odwołania się do zaktualizowanych pakietów biblioteki .NET Core. Metapackages są jako poprawek i aktualizacji z wersji `MAJOR` i `MINOR` dopasowania nowej wersji framework numerów wersji. Nowe nazwy framework docelowych z nowym `MAJOR.MINOR` wersji są dodawane do opisywania nowych interfejsów API (na przykład `netcoreapp2.1`). Nowe dystrybucji .NET Core jest publikowana z numeru wersji pasującego do `Microsoft.NETCore.App` metapackage.

### <a name="shipping-a-major-release"></a>Główna wersja wysyłania

Za każdym razem, gdy jest dostarczany w nowej wersji głównej .NET Core, `MAJOR` zwiększany pobiera numer wersji, a `MINOR` numer wersji jest resetowany do zera. Nowa wersja główna zawiera co najmniej wszystkich interfejsów API, które zostały dodane przez wersje pomocnicze po wcześniejszej wersji. Nowej wersji głównej należy włączyć ważne nowych scenariuszy, i może również porzucać obsługę starszych platformy.

Różne metapackages są aktualizowane w celu odwołania się do zaktualizowanych pakietów biblioteki .NET Core. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Metapackage i `netcore` platformy docelowej są numerów wersji jako pasujący dużej aktualizacji `MAJOR` numer wersji nowej wersji.

## <a name="see-also"></a>Zobacz także

[Platformy docelowe](../../standard/frameworks.md)  
[Tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md)  
[.NET core pomocy technicznej cyklu życia faktu arkusza](https://www.microsoft.com/net/core/support)  
[.NET core 2 + wersji powiązania](https://github.com/dotnet/designs/issues/3)  
