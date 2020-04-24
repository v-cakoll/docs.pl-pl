---
title: Sposób wersjonatów środowiska uruchomieniowego core i sdk .NET
description: W tym artykule dowiesz się, jak .NET Core SDK i Runtime są wersjona (podobnie jak semantyczne przechowywanie wersji).
ms.date: 07/26/2018
ms.openlocfilehash: f166a6dfc1c9127eb629365efd628855489a60cb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644395"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Omówienie wersji programu .NET Core

Program .NET Core odnosi się do środowiska uruchomieniowego .NET Core i zestawu .NET Core SDK, który zawiera narzędzia potrzebne do tworzenia aplikacji. Net Core SDK są przeznaczone do pracy z dowolną poprzednią wersją środowiska uruchomieniowego .NET Core. W tym artykule opisano środowisko wykonawcze i strategię wersji SDK. Wyjaśnienie numerów wersji dla programu .NET Standard można znaleźć w artykule wprowadzającym [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Środowisko uruchomieniowe .NET Core i zestaw SDK .NET Core dodają nowe funkcje w innym tempie — ogólnie rzecz biorąc, zestaw .NET Core SDK zapewnia zaktualizowane narzędzia szybciej niż środowisko uruchomieniowe .NET Core zmienia środowisko wykonawcze używane w produkcji.

## <a name="versioning-details"></a>Szczegóły przechowywania wersji

".NET Core 2.1" odnosi się do numeru wersji .NET Core Runtime. .NET Core Runtime ma główne/drobne/poprawki podejście do przechowywania wersji, które następuje [semantyczne przechowywanie wersji](#semantic-versioning).

.NET Core SDK nie jest zgodny z wersji semantycznych. .NET Core SDK zwalnia szybciej, a jego wersje muszą komunikować się zarówno wyrównane środowisko uruchomieniowe i sdk własnych wersji pomocniczych i poprawek. Pierwsze dwie pozycje wersji .NET Core SDK są zablokowane do środowiska uruchomieniowego .NET Core, z którym został wydany. Każda wersja SDK można tworzyć aplikacje dla tego środowiska wykonawczego lub dowolnej niższej wersji.

Trzecia pozycja numeru wersji zestawu SDK komunikuje zarówno numer pomocniczy, jak i numer poprawki. Wersja pomocnicza jest mnożona przez 100. Wersja pomocnicza 1, poprawka 2 będzie reprezentowana jako 102. Ostatnie dwie cyfry reprezentują numer poprawki. Na przykład wydanie platformy .NET Core 2.2 może tworzyć wersje, takie jak poniższa tabela:

| Change                | Środowisko uruchomieniowe platformy .NET Core | .NET Core SDK (\*) |
|-----------------------|-------------------|-------------------|
| Wersja początkowa       | 2.2.0             | 2.2.100           |
| Łatka SDK             | 2.2.0             | 2.2.101           |
| Poprawka środowiska wykonawczego i SDK | 2.2.1             | 2.2.102           |
| Zmiana funkcji SDK    | 2.2.1             | 2.2.200           |

(\*) Ten wykres używa 2.2 .NET Core Runtime jako przykład, ponieważ historyczny artefakt oznaczał, że pierwszy SDK dla .NET Core 2.1 to 2.1.300. Aby uzyskać więcej informacji, zobacz [wybór wersji .NET Core](selection.md).

Notatki:

- Jeśli pakiet SDK zawiera 10 aktualizacji funkcji przed aktualizacją funkcji środowiska uruchomieniowego, numery wersji są wprowadzane do serii 1000 z numerami takimi jak 2.2.1000 jako wersja funkcji po wersji 2.2.900. Nie oczekuje się, że taka sytuacja nastąpi.
- 99 wydań poprawek bez wydania funkcji nie nastąpi. Jeśli wydanie zbliża się do tej liczby, wymusza zwolnienie funkcji.

Więcej szczegółów można znaleźć w początkowej propozycji w repozytorium [dotnet/designs.](https://github.com/dotnet/designs/pull/29)

## <a name="semantic-versioning"></a>Przechowywanie wersji semantycznych

.NET Core *Runtime* z grubsza przylega do [semantycznego przechowywania wersji (SemVer),](https://semver.org/)przyjmując użycie `MAJOR.MINOR.PATCH` wersji, używając różnych części numeru wersji, aby opisać stopień i typ zmiany.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalne `PRERELEASE` `BUILDNUMBER` i części nigdy nie są częścią obsługiwanych wersji i istnieją tylko w kompilacjach nocnych, kompilacjach lokalnych z obiektów docelowych źródłowych i nieobsługiwałych wersji w wersji zapoznawczej.

### <a name="understand-runtime-version-number-changes"></a>Opis zmian numeru wersji środowiska wykonawczego

`MAJOR`zwiększa się, gdy:

- Znaczące zmiany występują w produkcie lub w nowym kierunku produktu.
- Podjęto przełomowe zmiany. Istnieje wysoka poprzeczka, aby zaakceptować przełomowe zmiany.
- Stara wersja nie jest już obsługiwana.
- Przyjęto `MAJOR` nowszą wersję istniejącej zależności.

`MINOR`zwiększa się, gdy:

- Zostanie dodana publiczna powierzchnia interfejsu API.
- Zostanie dodane nowe zachowanie.
- Przyjęto `MINOR` nowszą wersję istniejącej zależności.
- Wprowadzono nową zależność.

`PATCH`zwiększa się, gdy:

- Poprawki błędów są dokonywane.
- Dodano obsługę nowszej platformy.
- Przyjęto `PATCH` nowszą wersję istniejącej zależności.
- Każda inna zmiana nie pasuje do jednego z poprzednich przypadków.

Gdy istnieje wiele zmian, najwyższy element, którego dotyczą poszczególne zmiany, jest zwiększany, a następujące są resetowane do zera. Na przykład, `MAJOR` gdy jest `MINOR` zwiększany `PATCH` i są resetowane do zera. Gdy `MINOR` jest zwiększany, `PATCH` jest resetowany `MAJOR` do zera, podczas gdy pozostaje nietknięty.

## <a name="version-numbers-in-file-names"></a>Numery wersji w nazwach plików

Pliki pobrane dla .NET Core zawierają wersję, na przykład `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Wersje zapoznawcza

Wersje w `-preview[number]-([build]|"final")` wersji zapoznawczej mają dołączone do wersji. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Wersje serwisowe

Po wydaniu gaśnie, gałęzie wydania zazwyczaj przestać produkować codzienne kompilacje i zamiast tego rozpocząć produkcję kompilacji obsługi. Wersje obsługi mają `-servicing-[number]` dołączone do wersji. Na przykład `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relacja z wersjami standardowymi platformy .NET

.NET Standard składa się z zestawu odwołania .NET. Istnieje wiele implementacji specyficznych dla każdej platformy. Zestaw referencyjny zawiera definicję interfejsów API platformy .NET, które są częścią danej wersji .NET Standard. Każda implementacja spełnia kontrakt .NET Standard na określonej platformie. Więcej informacji o programie .NET Standard można dowiedzieć się więcej w artykule o [standardzie .NET](../../standard/net-standard.md) w przewodniku .NET.

Zestaw referencyjny .NET Standard `MAJOR.MINOR` używa schematu przechowywania wersji. `PATCH`level nie jest przydatne dla platformy .NET Standard, ponieważ udostępnia tylko specyfikację interfejsu API (bez implementacji) i z `MINOR` definicji wszelkie zmiany w interfejsie API będą stanowić zmianę w zestawie funkcji, a tym samym nową wersję.

Implementacje na każdej platformie mogą być aktualizowane, zazwyczaj w ramach wydania platformy, a zatem nie jest oczywiste dla programistów korzystających z platformy .NET Standard na tej platformie.

Każda wersja programu .NET Core implementuje wersję programu .NET Standard. Implementowanie wersji programu .NET Standard oznacza obsługę poprzednich wersji programu .NET Standard. Wersja .NET Standard i .NET Core niezależnie. To zbieg okoliczności, że .NET Core 2.0 implementuje .NET Standard 2.0. .NET Core 2.1 implementuje również .NET Standard 2.0. Program .NET Core będzie obsługiwał przyszłe wersje programu .NET Standard w miarę ich udostępniania.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | do 1,6     |
| 2.0       | do 2,0     |
| 2.1       | do 2,0     |
| 2.2       | do 2,0     |
| 3.0       | do 2,1     |

## <a name="see-also"></a>Zobacz też

- [Platformy docelowe](../../standard/frameworks.md)
- [Tworzenie pakietów dystrybucji platformy .NET Core](../distribution-packaging.md)
- [Arkusz informacyjny cyklu życia podstawowego cyklu pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy)
- [Powiązanie wersji .NET Core 2+](https://github.com/dotnet/designs/issues/3)
- [Obrazy platformy Docker dla platformy .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
