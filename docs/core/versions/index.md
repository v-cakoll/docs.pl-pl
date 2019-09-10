---
title: Jak działa wersja środowiska uruchomieniowego .NET Core i zestawu SDK
description: W tym artykule omówiono sposób wersji zestaw .NET Core SDK i środowiska uruchomieniowego (podobnie jak w przypadku wersji semantycznych).
author: bleroy
ms.date: 07/26/2018
ms.custom: seodec18
ms.openlocfilehash: 4674cd8750f5a5e628945c1712ac579d88385b94
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849284"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Omówienie wersji platformy .NET Core

.NET Core odwołuje się do środowiska uruchomieniowego .NET Core i zestaw .NET Core SDK, które zawiera narzędzia potrzebne do tworzenia aplikacji. Zestawy SDK platformy .NET Core są przeznaczone do pracy z dowolną poprzednią wersją środowiska uruchomieniowego platformy .NET Core. W tym artykule opisano strategię środowiska uruchomieniowego i wersji zestawu SDK. Informacje o numerach wersji .NET Standard można znaleźć w artykule wprowadzającym [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Środowisko uruchomieniowe platformy .NET Core i zestaw .NET Core SDK dodawać nowe funkcje z zastosowaniem różnych stawek ogólnie zestaw .NET Core SDK udostępniają zaktualizowane narzędzia szybciej niż środowisko uruchomieniowe programu .NET Core zmienia środowisko uruchomieniowe używane w środowisku produkcyjnym.

## <a name="versioning-details"></a>Szczegóły dotyczące wersji

".NET Core 2,1" odwołuje się do numeru wersji środowiska uruchomieniowego platformy .NET Core. Środowisko uruchomieniowe programu .NET Core ma rozwiązane podstawowe/drobne/poprawka do wersji, która następuje po [wersji semantycznej](#semantic-versioning).

Zestaw .NET Core SDK nie jest zgodna z wersją semantyczną. Zestaw .NET Core SDK wersje szybsze i jego wersje muszą komunikować się zarówno z wyrównanym środowiskiem uruchomieniowym, jak i wersjami pomocniczymi i poprawkami zestawu SDK. Pierwsze dwa pozycje wersji zestaw .NET Core SDK są blokowane dla środowiska uruchomieniowego platformy .NET Core wydanego za pomocą programu. Każda wersja zestawu SDK może tworzyć aplikacje dla tego środowiska uruchomieniowego lub dowolnej niższej wersji.

Trzecia pozycja numeru wersji zestawu SDK komunikuje się zarówno z literą, jak i numerem poprawki. Wersja pomocnicza jest mnożona przez 100. Wersja pomocnicza 1, Poprawka wersja 2 byłaby reprezentowana jako 102. Ostatnie dwie cyfry reprezentują numer poprawki. Na przykład wydanie programu .NET Core 2,2 może tworzyć wersje, takie jak Następująca tabela:

| Zmiana                | Środowisko uruchomieniowe platformy .NET Core | Zestaw .NET Core SDK (*) |
|-----------------------|-------------------|-------------------|
| Wersja początkowa       | 2.2.0             | 2.2.100           |
| Poprawka zestawu SDK             | 2.2.0             | 2.2.101           |
| Środowisko uruchomieniowe i poprawka zestawu SDK | 2.2.1             | 2.2.102           |
| Zmiana funkcji zestawu SDK    | 2.2.1             | 2.2.200           |

(\*) Ten wykres używa przyszłych 2,2 środowiska uruchomieniowego platformy .NET Core jako przykładu, ponieważ artefakt historyczny mający pierwszy zestaw SDK dla platformy .NET Core 2,1 to 2.1.300. Aby uzyskać więcej informacji, zobacz [wybór wersji platformy .NET Core](selection.md).

O

- Jeśli zestaw SDK ma 10 aktualizacji funkcji przed aktualizacją funkcji środowiska uruchomieniowego, numery wersji są przydzielone do serii 1000 z liczbami takimi jak 2.2.1000 jako wersja funkcji po 2.2.900. Ta sytuacja nie powinna wystąpić.
- 99 wersje poprawek bez wydania funkcji nie zostaną wykonane. Jeśli wersja zbliża się do tej liczby, wymusza wydanie funkcji.

Więcej szczegółów można znaleźć w wstępnej propozycji w repozytorium [dotnet/Designing](https://github.com/dotnet/designs/pull/29) .

## <a name="semantic-versioning"></a>Wersja semantyczna

*Środowisko uruchomieniowe* programu .NET Core jest w przybliżeniu zgodne z [wersją semantyki (SemVer)](https://semver.org/), `MAJOR.MINOR.PATCH` przy użyciu różnych części numeru wersji do opisania stopnia i typu zmiany.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalne `PRERELEASE` i`BUILDNUMBER` części nie są nigdy częścią obsługiwanych wersji i istnieją tylko w przypadku nocnych kompilacji, lokalne kompilacje ze źródłowych elementów docelowych i nieobsługiwane wersje wersji zapoznawczej.

### <a name="understand-runtime-version-number-changes"></a>Informacje o zmianach numeru wersji środowiska uruchomieniowego

`MAJOR`jest zwiększana, gdy:

- Wprowadzono znaczące zmiany w produkcie lub nowy kierunek produktu.
- Wprowadzono istotne zmiany. Istnieje wysoki poziom akceptowania istotnych zmian.
- Stara wersja nie jest już obsługiwana.
- Przyjęto `MAJOR` nowszą wersję istniejącej zależności.

`MINOR`jest zwiększana, gdy:

- Dodano publiczny obszar powierzchni interfejsu API.
- Zostanie dodane nowe zachowanie.
- Przyjęto `MINOR` nowszą wersję istniejącej zależności.
- Zostanie wprowadzona nowa zależność.

`PATCH`jest zwiększana, gdy:

- Wprowadzono poprawki błędów.
- Dodano obsługę nowszej platformy.
- Przyjęto `PATCH` nowszą wersję istniejącej zależności.
- Jakakolwiek inna zmiana nie pasuje do jednego z poprzednich przypadków.

W przypadku zmiany wielu zmian najwyższy element, na który wpływają poszczególne zmiany, jest zwiększany, a następujące są resetowane do zera. Na przykład gdy `MAJOR` jest zwiększana, `MINOR` i `PATCH` są resetowane do zera. Gdy `MINOR` jest zwiększana, `PATCH` jest resetowana do zera `MAJOR` , podczas gdy pozostaje nienaruszony.

## <a name="version-numbers-in-file-names"></a>Numery wersji w nazwach plików

Pliki pobrane dla platformy .NET Core przenoszą wersję, na przykład `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Wersje zapoznawcze

Wersje zapoznawcze mają `-preview[number]-([build]|"final")` dołączony do wersji. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Wersje obsługi

Po wyjściu z wersji, gałęzie wydań zwykle zatrzymują codzienne kompilacje i zamiast tego uruchamiają kompilacje obsługi. Wersje obsługujące zostały `-servicing-[number]` dołączone do wersji. Na przykład `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relacja z wersjami .NET Standard

.NET Standard składa się z zestawu odwołań platformy .NET. Istnieje wiele implementacji specyficznych dla każdej platformy. Zestaw odwołań zawiera definicję interfejsów API platformy .NET, które są częścią danej .NET Standard wersji. Każda implementacja spełnia umowę .NET Standard na określonej platformie. Więcej informacji na temat .NET Standard można znaleźć w artykule na [.NET Standard](../../standard/net-standard.md) w przewodniku po platformie .NET.

Zestaw odwołań .NET Standard używa `MAJOR.MINOR` schematu przechowywania wersji. `PATCH`poziom nie jest użyteczny w przypadku .NET Standard, ponieważ uwidacznia tylko specyfikację interfejsu API (bez implementacji) i według definicji jakakolwiek zmiana w interfejsie API będzie reprezentować zmianę zestawu funkcji i `MINOR` w związku z tym nową wersją.

Implementacje na każdej platformie mogą być aktualizowane, zazwyczaj jako część wersji platformy, i nie są widoczne dla programistów używających .NET Standard na tej platformie.

Każda wersja programu .NET Core implementuje wersję .NET Standard. Zaimplementowanie wersji .NET Standard oznacza obsługę wcześniejszych wersji .NET Standard. Niezależna wersja .NET Standard i .NET Core. Jest to współdziałanie, które program .NET Core 2,0 implementuje .NET Standard 2,0. Platforma .NET Core 2,1 implementuje również .NET Standard 2,0. Platforma .NET Core będzie obsługiwała przyszłe wersje .NET Standard, gdy staną się dostępne.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | do 1,6     |
| 2.0       | do 2,0     |
| 2.1       | do 2,0     |

## <a name="see-also"></a>Zobacz także

- [Platformy docelowe](../../standard/frameworks.md)
- [Tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md)
- [Arkusz faktów cyklu życia obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy)
- [Powiązanie z platformą .NET Core 2 +](https://github.com/dotnet/designs/issues/3)
- [Obrazy platformy Docker dla programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
