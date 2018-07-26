---
title: Przechowywanie wersji platformy .NET core
description: Dowiedz się, jak działa wersji platformy .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 02/13/2018
ms.openlocfilehash: aa4f05a1a95c1bfbd16f41ca695ea23d48606772
ms.sourcegitcommit: 702d5ffc6e733b6c4ded85bf1c92e2293638ee9a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/04/2018
ms.locfileid: "37792325"
---
# <a name="net-core-versioning"></a>Przechowywanie wersji platformy .NET core

.NET core składa się z [pakiety NuGet](../packages.md), narzędzi i platform, które są dystrybuowane jako jednostka. Każdego z tych warstw platformy może być wersjonowany oddzielnie, umożliwiając lepsze elastyczność. Pewien stopień elastyczności znaczące przechowywania wersji, w tym zakresie, jest również dążenie do wersji platformy jako jednostka do sprawiają, że produkt jest łatwiejsze do zrozumienia.

Celem jest wyjaśnienie, jak zestaw .NET Core SDK i środowisko uruchomieniowe są wersjonowane w tym artykule.

Istnieje wiele ruchomych części tej wersji niezależnie od siebie platformie .NET Core. Jednak począwszy od programu .NET Core 2.0 jest łatwy do zrozumienia numer wersji najwyższego poziomu każdy rozumie, aby można *wersji* ".NET Core" jako całość. Pozostała część tego dokumentu przechodzi w stan szczegółowe informacje o wersji tych części. Informacje te mogą być ważne, jeśli na przykład masz Menedżera pakietów.

> [!IMPORTANT]
> Szczegóły wersji opisane w tym temacie nie mają zastosowania do bieżącej wersji programu .NET Core SDK i środowiska uruchomieniowego.
> Schemat wersja ulega zmianie w przyszłych wersjach. Możesz zobaczyć bieżące wniosek na [dotnet/projekty](https://github.com/dotnet/designs/pull/29) repozytorium.

## <a name="versioning-details"></a>Szczegóły wersji

Przy użyciu platformy .NET Core 2.0 pliki do pobrania Pokaż numeru wersji pojedynczego w nazwie pliku. Ujednolicone zostały następujące numery wersji:

* Udostępnione środowisko i skojarzone środowiska uruchomieniowego.
* Zestaw .NET Core SDK i skojarzony interfejsu wiersza polecenia platformy .NET Core.
* `Microsoft.NETCore.App` Meta Microsoft.aspnetcore.all.

Korzystanie z jednej wersji numer sprawia, że łatwiejsze dla użytkowników dowiedzieć się, jakie wersje zestawu SDK do zainstalowania na swoich komputerach deweloperskich i jakie odpowiednią wersję udostępnionej platformy należy go po przejściu do trybu czasu do aprowizowania w środowisku produkcyjnym. Podczas pobierania zestawu SDK lub środowisko uruchomieniowe, numer wersji, który zostanie wyświetlony będzie taka sama.

### <a name="version-selection"></a>Wybór wersji

.NET core stosuje zestaw zasad, które określają, które wersje środowiska uruchomieniowego .NET Core i zestawu SDK są używane w różnych scenariuszach. Te scenariusze i zasady są w pełni przedstawione w artykule na [wybór wersji](selection.md).

Można potraktować te zasady, zgodnie z wykonaniem następujących ról:

* Włącz łatwe i efektywne wdrażanie programu .NET Core, w tym zabezpieczeń i niezawodności aktualizacji.
* Umożliwiają deweloperom używanie najnowsze narzędzia i polecenia niezależnie od docelowego środowiska uruchomieniowego.

### <a name="installers"></a>Pliki instalacyjne

Za pomocą platformy .NET Core 2.0, pliki do pobrania dla [codzienne kompilacje](https://github.com/dotnet/core-setup#daily-builds) i [zwalnia](https://www.microsoft.com/net/download/core) stosować nowy schemat nazewnictwa, która jest łatwiejsze do zrozumienia.
Interfejs użytkownika Instalatora w tych plikach do pobrania również została zmodyfikowana w celu wyraźnie stwarzać nazwy i wersje są zainstalowane składniki. W szczególności tytuły pokazują teraz ten sam numer wersji, który jest w nazwie pliku pliki do pobrania.

#### <a name="file-name-format"></a>Format nazwy pliku

`[product]-[component]-[major].[minor].[patch]-[previewN]-[optional build #]-[rid].[file ext]`

Poniżej przedstawiono kilka przykładów tego formatu:

```
dotnet-runtime-2.0.4-osx.10.12-x64.pkg            # Mac runtime installer
dotnet-sdk-2.0.4-win-x64.exe                      # Windows SDK installer
dotnet-sdk-2.0.4-linux-x64.tar.gz                 # Linux binary archive

#Ubuntu file set needed for the SDK
dotnet-host-2.0.4-ubuntu.16.04-x64.deb            # Host / muxer and host policy
dotnet-runtime-2.0.4-ubuntu.16.04-x64.deb         # runtime
dotnet-sdk-2.0.4-ubuntu.16.04-x64.deb             # SDK tools
```

Format można odczytać i wyraźnie pokazuje, jakie są pobierane, jaka wersja jest i gdzie można go użyć. Nazwa pakietu środowiska uruchomieniowego zawiera `runtime`, a zestaw SDK zawiera `SDK`.

#### <a name="ui-string-format"></a>Format ciągu interfejsu użytkownika

Wszystkie witryny sieci web, opisy i ciągi interfejsu użytkownika w instalatory pozostają spójne, dokładne i proste. W poniższej tabeli przedstawiono kilka przykładów:

| Instalator | Tytuł okna                          | Innej zawartości w Instalatorze | Co to jest zainstalowany                               |
| :--       | :--                                   | :--                        | :--                                             |
| SDK       | Instalator programu .NET core 2.0 SDK (x 64)     | .NET core 2.0.4 zestawu SDK        | .NET Core 2.0.4 Tools + .NET Core 2.0.4 Runtime |
| Środowisko uruchomieniowe   | Środowisko uruchomieniowe (x64) Instalatora programu .NET core 2.0 | .NET Core 2.0.4 Runtime    | .NET Core 2.0.4 Runtime                         |

Wersje zapoznawcze nieco tylko:

| Instalator | Tytuł okna                                    | Innej zawartości w Instalatorze        | Co to jest zainstalowany                                                   |
| :--       | :--                                             | :--                               | :--                                                                 |
| SDK       | Instalatora programu .NET core 2.0 (wersja zapoznawcza 1) zestawu SDK (x 64)     | 1 — zestaw SDK platformy .NET core 2.0.0 w wersji zapoznawczej     | Narzędzia programu .NET core 2.0.0 (wersja zapoznawcza 1) + platformy .NET Core 2.0.0 w wersji zapoznawczej 1 środowiska uruchomieniowego |
| Środowisko uruchomieniowe   | Środowisko uruchomieniowe (x64) Instalatora programu .NET core 2.0 (wersja zapoznawcza 1) | Środowisko uruchomieniowe programu .NET core 2.0.0 1 (wersja zapoznawcza) | Środowisko uruchomieniowe programu .NET core 2.0.0 1 (wersja zapoznawcza)                                   |

Może się zdarzyć, że wersja zestawu SDK zawiera więcej niż jedna wersja środowiska uruchomieniowego. Jeśli tak się stanie, Instalator UX wygląda podobnie do poniższego (tylko wersja zestawu SDK jest wyświetlany i zainstalowanych wersji środowiska uruchomieniowego są wyświetlane na stronie podsumowania pod koniec procesu instalacji na Windows i Mac):

| Instalator | Tytuł okna                      | Innej zawartości w Instalatorze                                   | Co to jest zainstalowany                                                         |
| :--       | :--                               | :--                                                          | :--                                                                       |
| SDK       | Instalator programu .NET core 2.1 zestawu SDK (x 64) | .NET Core 2.1.1 SDK <br> .NET Core 2.1.1 Runtime <br> Środowisko uruchomieniowe programu .NET core 2.0.6 | Narzędzia programu .NET core 2.1.1, środowisko uruchomieniowe programu .NET Core 2.1.1 i środowisko uruchomieniowe programu .NET Core 2.0.6 |

Istnieje również możliwość, że podstawowe narzędzia .NET muszą zostać zaktualizowane, bez zmiany środowiska uruchomieniowego. W takim przypadku zwiększa się wersja zestawu SDK (na przykład, aby 2.1.2), a następnie środowiska uruchomieniowego następnym razem go przechwycił dostarczany (na przykład, środowisko uruchomieniowe i zestaw SDK dostarczanie przy następnym jako 2.1.3).

### <a name="package-managers"></a>Menedżery pakietów

.NET core mogą być dystrybuowane przez inne jednostki niż firmy Microsoft. W szczególności właściciele dystrybucji systemu Linux i maintainers pakietu mogą dodawać pakiety platformy .NET Core do ich menedżerów pakietów. Aby uzyskać zalecenia dotyczące sposobu te pakiety powinna być nazwane i kontrolą wersji, zobacz [tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md).

#### <a name="minimum-package-set"></a>Ustaw minimalną pakietu

* `dotnet-runtime-[major].[minor]`: środowisko uruchomieniowe o określonej wersji (tylko najnowsza wersja poprawki dla danej głównych + pomocnicza kombinacji powinny być dostępne w Menedżerze pakietów). Nowe wersje poprawki pakietu aktualizacji, ale nowe wersje drobnych lub główne są oddzielne pakiety.

  **Zależności**: `dotnet-host`

* `dotnet-sdk`: najnowszy zestaw SDK. `update` Przekazuj głównych i pomocniczych oraz stosowanie poprawek do wersji.

  **Zależności**: r `dotnet-sdk-[major].[minor]`.

* `dotnet-sdk-[major].[minor]`: zestaw SDK o określonej wersji. Określona wersja jest najwyższa wersja uwzględnione uwzględnione struktur udostępnionych, tak, aby użytkownicy mogą łatwo odnoszą się zestaw SDK do udostępnionej platformy. Nowe wersje poprawki pakietu aktualizacji, ale nowe wersje drobnych lub główne są oddzielne pakiety.

  **Zależności**: `dotnet-host`, co najmniej jeden `dotnet-runtime-[major].[minor]` (jeden z nich jest używany przez sam kod zestawu SDK pozostałe wersje to tutaj dla użytkowników skompilować i uruchomić względem).

* `dotnet-host`: najnowsze hosta.

##### <a name="preview-versions"></a>Wersje (wersja zapoznawcza)

Pakiet maintainers może zdecydować o zawierają wersje środowiska uruchomieniowego i zestawu SDK w wersji zapoznawczej. Nie dołączaj tych wersji zapoznawczych niewersjonowanego `dotnet-sdk` pakietu, ale można je zwolnić jako numerów wersji pakietów ze znacznikiem dodatkowe podglądu dołączany do nazwy sekcji wersji głównych i pomocniczych. Na przykład mogą istnieć `dotnet-sdk-2.0-preview1-final` pakietu.

### <a name="docker"></a>Docker

Ogólne Docker tag konwencji nazewnictwa jest umieścić numer wersji przed nazwą składnika. Ta konwencja mogą nadal być wykorzystywane. Bieżące znaczniki zawierają tylko wersja środowiska uruchomieniowego w następujący sposób.

* 1.0.8-Runtime
* 1.0.8-sdk
* 2.0.4-runtime
* 2.0.4-sdk
* 2.1.1-Runtime
* 2.1.1-sdk

Tagi SDK powinien zostać zaktualizowany do reprezentowania wersji zestawu SDK, a nie środowiska uruchomieniowego.

Istnieje również możliwość, usunięto narzędzia wiersza polecenia platformy .NET Core (dołączony do zestawu SDK) ale reship istniejących plików wykonywalnych. W takim przypadku zwiększa się wersja zestawu SDK (na przykład, aby 2.1.2), a następnie środowiska uruchomieniowego następnym razem go przechwycił dostarczany (na przykład, środowisko uruchomieniowe i zestaw SDK dostarczanie następującym czasie jako 2.1.3).

## <a name="semantic-versioning"></a>Semantic Versioning

Korzysta z platformy .NET core [Semantic Versioning (SemVer)](http://semver.org/), przyjęcie użytkowania `MAJOR.MINOR.PATCH` przechowywania wersji, użycie różnych części numeru wersji w celu opisania stopnia i typ zmiany.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalny `PRERELEASE` i `BUILDNUMBER` części nigdy nie są częścią obsługiwanych wersji i istnieją tylko na nocnych kompilacji, lokalne kompilacje z celów źródła i nieobsługiwane wersje zapoznawcze.

### <a name="how-version-numbers-are-incremented"></a>Jak są zwiększane numery wersji?

`MAJOR` jest zwiększany, gdy:

- Stara wersja nie jest już obsługiwana.
- Nowsze `MAJOR` przyjmuje się wersja istniejące zależności.
- Domyślne ustawienie niedoskonałość zgodności jest zmieniana na "wyłączone".

`MINOR` jest zwiększany, gdy:

- Publiczny obszar powierzchni interfejsu API jest dodawany.
- Nowe zachowanie jest dodawany.
- Nowsze `MINOR` przyjmuje się wersja istniejące zależności.
- Wprowadzono nowe zależności.

`PATCH` jest zwiększany, gdy:

- Poprawki zostały wprowadzone.
- Zostanie dodana jego obsługa dla nowszej platformy.
- Nowsze `PATCH` przyjmuje się wersja istniejące zależności.
- Inne zmiany nie mieści się jednego z poprzednich przypadków.

W przypadku wielu zmian najwyższy element wpływ poszczególnych zmian jest zwiększany, a poniższych jest resetowany do zera. Na przykład, gdy `MAJOR` jest zwiększany `MINOR` i `PATCH` jest resetowany do zera. Gdy `MINOR` jest zwiększany `PATCH` jest resetowany do zera trochę `MAJOR` nie została zmieniona po lewej.

### <a name="preview-versions"></a>Wersje (wersja zapoznawcza)

Wersji zapoznawczych mają `-preview[number]-([build]|"final")` dołączany do wersji. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Obsługa wersji

Po wydaniu trafia, gałęzie wydań jest ogólnie Zatrzymaj tworzenie codzienne kompilacje i zamiast tego zaczniesz tworzenie obsługi kompilacji. Wersje obsługi mają `-servicing-[number]` dołączany do wersji. Na przykład `2.0.1-servicing-006924`.

### <a name="lts-vs-current"></a>LTS, a bieżąca

Istnieją dwa pociągów wersji dla platformy .NET Core: długi okres pomocy technicznej (LTS) i bieżący. Który umożliwia użytkownikom na wybranie poziomu stabilności i nowe funkcje, które zechcą, podczas nadal obsługiwane.

- LTS oznacza mniejszą częstotliwością uzyskuj nowe funkcje, ale masz bardziej dojrzałych platformy. LTS ma również dłuższy okres wsparcia.
- Bieżąca oznacza, że możesz korzystać z nowych funkcji i interfejsów API częściej, ale wadą jest to, że masz krótsze okno czasu na zainstalowanie aktualizacji i te aktualizacje możliwe częściej. Bieżący jest również w pełni obsługiwane, ale czas pomocy technicznej jest krótszy niż LTS.

"Bieżącej" wersji może uzyskać podwyższony do LTS.

"LTS" i "Aktualne" powinny być uważane etykiety, które umieściliśmy w określonych wydaniach zapewnienie instrukcji o skojarzone poziom pomocy technicznej.

Aby uzyskać więcej informacji, zobacz [.NET Core pomocy technicznej cyklu życia zestawieniem](https://www.microsoft.com/net/core/support).

## <a name="versioning-scheme-details"></a>Szczegóły schematu przechowywania wersji

.NET core składa się z następujących elementów:

- Host: albo *dotnet.exe* zależny od struktury aplikacji, lub  *\<nazwa_aplikacji > .exe* niezależna aplikacji.
- Zestaw SDK (zestaw narzędzi niezbędnych na komputerze dewelopera, ale nie w środowisku produkcyjnym).
- Środowisko uruchomieniowe.
- Implementacja udostępnionej platformy rozpowszechniane w formie pakietów. Każdy pakiet jest wersjonowany niezależnie, szczególnie w przypadku wersji poprawki.
- Opcjonalnie, zbiór [metapakiety](../packages.md) , odwołania się do szczegółowych pakietów jako jednostka numerów wersji. Metapakiety może być wersjonowany niezależnie od pakietów.

.NET core zawiera także zestaw platform docelowych (na przykład `netstandard` lub `netcoreapp`) reprezentujące stopniowo większy zestaw interfejsów API, jak numery wersji są zwiększane.

### <a name="net-standard"></a>.NET standard

.NET standard używał `MAJOR.MINOR` schematu przechowywania wersji. `PATCH` poziom nie jest przydatne dla platformy .NET Standard, ponieważ wyraża zestaw umowy, które są postanowiliśmy rzadziej i nie Prezentuj takie same wymagania dotyczące wersji jako rzeczywiste wdrożenie.

Nie ma żadnych rzeczywistych sprzężenie wersje .NET Standard i .NET Core: .NET Core 2.0, stanie się z implementacji .NET Standard 2.0, ale nie ma żadnej gwarancji, że przyszłych wersjach programu .NET Core będzie zmapowana do tej samej wersji .NET Standard. .NET core może wysłać interfejsów API, które nie są zdefiniowane przez .NET Standard, a w efekcie może dostarczanie nowych wersji bez konieczności nowe .NET Standard. .NET standard jest również pojęcie, która ma zastosowanie do innych celów, takich jak .NET Framework lub platformy Mono, nawet wtedy, gdy jego powstania stało się pokrywać się z zakresem platformy .NET Core.

### <a name="packages"></a>Pakiety

Ewolucji pakietów biblioteki i wersji niezależnie. Pakiety, które pokrywają się z .NET Framework System. \* zestawy zazwyczaj używają wersji 4.x, dopasowanie się do wersji 4.x .NET Framework (wybór historycznych). Pakiety, które nie nakładają się z bibliotekami .NET Framework (na przykład [ `System.Reflection.Metadata` ](https://www.nuget.org/packages/System.Reflection.Metadata)) zazwyczaj rozpoczynają się od wersji 1.0 i zwiększ z tego miejsca.

Pakiety opisanego przez [ `NETStandard.Library` ](https://www.nuget.org/packages/NETStandard.Library) traktowania specjalnie ze względu na podstawowej platformy.

`NETStandard.Library` pakiety będzie zazwyczaj wersji jako zestaw, ponieważ mają one poziomie implementacji zależności między nimi.

### <a name="metapackages"></a>Metapakiety

Przechowywanie wersji platformy .NET Core metapakiety zależy od wersji platformy .NET Core, są one częścią.

Na przykład, metapakiety w programie .NET Core 2.1.3 powinny wszystkie mieć 2.1 jako ich `MAJOR` i `MINOR` numerów wersji.

Wersja poprawki meta Microsoft.aspnetcore.all jest zwiększany za każdym razem, gdy zaktualizowaniu dowolnego pakietu odwołania. Wersje poprawki nie zawierają zaktualizowaną wersję. W rezultacie metapakiety ściśle są niezgodne z SemVer, ponieważ jego schemat przechowywania wersji nie stanowią stopień zmian w pakietach podstawowego, ale przede wszystkim z poziomu interfejsu API.

Obecnie istnieją dwa podstawowe metapakiety dla platformy .NET Core:

**Microsoft.NETCore.App**

- V1.0, począwszy od platformy .NET Core 1.0 (te wersje są zgodne).
- Mapuje `netcoreapp` framework.
- W tym artykule opisano pakietów dystrybucji platformy .NET Core.

Uwaga: [ `Microsoft.NETCore.Portable.Compatibility` ](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) jest inny meta Microsoft.aspnetcore.all platformy .NET Core, który istnieje w celu włączenia zgodności przy użyciu standardowej implementacji .NET wstępne platformy .NET. Go nie jest mapowany do określonej struktury, więc jego wersji, takich jak pakiet.

**NETStandard.Library**

[`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) w tym artykule opisano bibliotek, które są częścią [.NET Standard](../../standard/library.md). Ma zastosowanie do wszystkich implementacje platformy .NET, które obsługują .NET Standard, takich jak .NET Framework i .NET Core, Mono.

### <a name="target-frameworks"></a>Platformy docelowe

TARGET framework w wersji są aktualizowane, gdy zostaną dodane nowe interfejsy API. Mają one koncepcja wersja poprawki zabezpieczeń, ponieważ stanowią one kształt interfejsu API i nie dotyczy wdrożenia. Przechowywanie wersji głównych i pomocniczych regułom SemVer określonej wcześniej i pokrywa się z `MAJOR` i `MINOR` liczby dystrybucji platformy .NET Core, które je implementują.

## <a name="versioning-in-practice"></a>Przechowywanie wersji w praktyce

Po pobraniu platformy .NET Core, nazwa pobranego pliku niesie ze sobą wersji, na przykład `dotnet-sdk-2.0.4-win10-x64.exe`.

Brak zatwierdzeń i żądań ściągnięcia z repozytoriów platformy .NET Core w usłudze GitHub codziennie, co nowe kompilacje wiele bibliotek. Nie jest praktyczne utworzyć nowy wersjach publicznych platformy .NET Core dla każdej zmiany. Zamiast tego zmiany są agregowane przez nieokreślony czas (na przykład, tygodni lub miesięcy) przed wprowadzeniem nowej publicznej stabilnej wersji platformy .NET Core.

Nowa wersja programu .NET Core może oznaczać, że kilka rzeczy:

- Nowe wersje pakietów i metapakiety.
- Nowe wersje różnych platform, zakładając, że dodanie nowych interfejsów API.
- Nowa wersja dystrybucji platformy .NET Core.

### <a name="shipping-a-patch-release"></a>Wysyłanie wydaniu poprawek

Po wysyłania głównej wersji programu .NET Core w wersji 2.0.0, np. poziom poprawki zmian do bibliotek .NET Core, aby naprawić błędy i zwiększyć wydajność i niezawodność. Oznacza to, że zostały wprowadzone nie nowe interfejsy API. Różne metapakiety zostaną zaktualizowane do odniesienia zaktualizowanych pakietów biblioteki .NET Core. Metapakiety są określane jako poprawki, aktualizacje (`MAJOR.MINOR.PATCH`). Platformy docelowe nigdy nie są aktualizowane w ramach wersji poprawki. Nowe dystrybucji platformy .NET Core jest zwolniony z numeru wersji, który jest zgodny z typem `Microsoft.NETCore.App` meta Microsoft.aspnetcore.all.

### <a name="shipping-a-minor-release"></a>Wysyłanie wersję pomocniczą

Po wysyłania wersji platformy .NET Core z zwiększona `MAJOR` numer wersji, nowe interfejsy API są dodawane do biblioteki .NET Core, aby umożliwić obsługę nowych scenariuszy. Różne metapakiety zostaną zaktualizowane do odniesienia zaktualizowanych pakietów biblioteki .NET Core. Metapakiety są określane jako aktualizacje poprawek za pomocą `MAJOR` i `MINOR` numery wersji dopasowania wersję szablonu. Nowe nazwy framework docelowej przy użyciu nowego `MAJOR.MINOR` wersji są dodawane do opisania nowe interfejsy API (na przykład `netcoreapp2.1`). Nowe dystrybucji platformy .NET Core jest zwolniony z zgodnych numer wersji do `Microsoft.NETCore.App` meta Microsoft.aspnetcore.all.

### <a name="shipping-a-major-release"></a>Wysyłanie głównej wersji

Za każdym razem, gdy jest dostarczany nowej wersji głównej programu .NET Core, `MAJOR` zwiększany pobiera numer wersji, a `MINOR` numer wersji jest resetowany do zera. Nowa wersja główna zawiera co najmniej wszystkie interfejsy API, które zostały dodane w wersji pomocniczej po wcześniejszej wersji głównej. Nowej wersji głównej, należy włączyć ważnych nowych scenariuszy i może również porzucać obsługę starszych platformy.

Różne metapakiety zostaną zaktualizowane do odniesienia zaktualizowanych pakietów biblioteki .NET Core. [ `Microsoft.NETCore.App` ](https://www.nuget.org/packages/Microsoft.NETCore.App) Meta Microsoft.aspnetcore.all i `netcore` platformy docelowej są określane jako ważna aktualizacja odpowiadający mu `MAJOR` numer wersji nowej wersji.

## <a name="see-also"></a>Zobacz także

[Platformy docelowe](../../standard/frameworks.md)  
[Tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md)  
[.NET core pomocy technicznej cyklu życia faktu arkusza](https://www.microsoft.com/net/core/support)  
[Wiązanie wersji programu .NET core 2 +](https://github.com/dotnet/designs/issues/3)  
