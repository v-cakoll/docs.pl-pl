---
title: Sposób wersjoniwywania programu .NET Core Runtime i SDK
description: W tym artykule nauczysz, jak są wersjonowane zestaw SDK .NET Core i runtime (podobnie jak przechowywanie wersji semantycznych).
ms.date: 07/26/2018
ms.openlocfilehash: c85a2112b439768068663688947960ac814de824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75777317"
---
# <a name="overview-of-how-net-core-is-versioned"></a>Omówienie wersji programu .NET Core

.NET Core odnosi się do programu .NET Core Runtime i .NET Core SDK, który zawiera narzędzia potrzebne do tworzenia aplikacji. Zestawy SDK .NET Core są przeznaczone do pracy z dowolną poprzednią wersją programu .NET Core Runtime. W tym artykule wyjaśniono, w czasie wykonywania i strategii wersji sdk. Wyjaśnienie numerów wersji dla .NET Standard można znaleźć w artykule wprowadzającym [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Zestaw .NET Core Runtime i .NET Core SDK dodają nowe funkcje z innym szybkością — ogólnie rzecz biorąc. Zestaw SDK .NET Core udostępnia zaktualizowane narzędzia szybciej niż program .NET Core Runtime zmienia czas pracy używanej w środowisku produkcyjnym.

## <a name="versioning-details"></a>Szczegóły dotyczące wersji

".NET Core 2.1" odnosi się do numeru wersji programu .NET Core Runtime. Program .NET Core Runtime ma główne/pomocnicze/łata podejście do wersji, które następuje [po wersji semantycznej](#semantic-versioning).

Zestaw SDK .NET Core nie jest zgodny z wersją semantyczną. Zestaw SDK .NET Core jest wydawany szybciej, a jego wersje muszą komunikować zarówno wyrównany czas wykonywania, jak i własne wersje pomocnicze i poprawki sdk. Pierwsze dwie pozycje sdk .NET Core są zablokowane do .NET Core Runtime, z których został wydany. Każda wersja sdk można tworzyć aplikacje dla tego czasu uruchomieniowego lub dowolnej niższej wersji.

Trzecia pozycja numeru wersji SDK komunikuje zarówno numer pomocniczy, jak i numer poprawki. Wersja pomocnicza jest mnożona przez 100. Wersja pomocnicza 1, poprawka w wersji 2 będzie reprezentowana jako 102. Dwie ostatnie cyfry reprezentują numer poprawki. Na przykład wydanie .NET Core 2.2 może tworzyć wersje, takie jak następująca tabela:

| Change                | Środowisko uruchomieniowe platformy .NET Core | Zestaw SDK rdzenia .NET (\*) |
|-----------------------|-------------------|-------------------|
| Wersja początkowa       | 2.2.0             | 2.2.100           |
| Łatka SDK             | 2.2.0             | 2.2.101           |
| Czas wykonywania i łatka SDK | 2.2.1             | 2.2.102           |
| Zmiana funkcji sdk    | 2.2.1             | 2.2.200           |

(\*) Ten wykres używa 2.2 .NET Core Runtime jako przykład, ponieważ historyczny artefakt oznaczało pierwszy zestaw SDK dla .NET Core 2.1 jest 2.1.300. Aby uzyskać więcej informacji, zobacz [wybór wersji .NET Core](selection.md).

Notatki:

- Jeśli zestaw SDK ma 10 aktualizacji funkcji przed aktualizacją funkcji czasu wykonywania, numery wersji są przekształcane w serię 1000 z numerami takimi jak 2.2.1000 jako wersja funkcji po 2.2.900. Ta sytuacja nie powinna wystąpić.
- 99 wersji poprawek bez wydania funkcji nie nastąpi. Jeśli wersja zbliża się do tego numeru, wymusza zwolnienie funkcji.

Więcej szczegółów można zobaczyć w początkowej propozycji w repozytorium [dotnet/designs.](https://github.com/dotnet/designs/pull/29)

## <a name="semantic-versioning"></a>Przechowywanie wersji semantycznych

.NET Core *Runtime* z grubsza przylega do [wersji semantycznej (SemVer),](https://semver.org/)przyjmując użycie `MAJOR.MINOR.PATCH` wersji, przy użyciu różnych części numeru wersji do opisania stopnia i typu zmiany.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalne `PRERELEASE` `BUILDNUMBER` i części nigdy nie są częścią obsługiwanych wersji i istnieją tylko na kompilacjach nocnych, lokalnych kompilacjach z obiektów docelowych źródłowych i nieobsługiwanych wersjach w wersji zapoznawczej.

### <a name="understand-runtime-version-number-changes"></a>Opis zmian numeru wersji w czasie wykonywania

`MAJOR`jest zwiększana, gdy:

- Istotne zmiany zachodzą w produkcie lub nowy kierunek produktu.
- Wprowadzono przełomowe zmiany. Akceptacja przełomowych zmian jest wysoka.
- Stara wersja nie jest już obsługiwana.
- Zostanie przyjęta `MAJOR` nowsza wersja istniejącej zależności.

`MINOR`jest zwiększana, gdy:

- Zostanie dodany publiczny obszar powierzchni interfejsu API.
- Zostanie dodane nowe zachowanie.
- Zostanie przyjęta `MINOR` nowsza wersja istniejącej zależności.
- Wprowadzono nową zależność.

`PATCH`jest zwiększana, gdy:

- Poprawki błędów są dokonywane.
- Dodano obsługę nowszej platformy.
- Zostanie przyjęta `PATCH` nowsza wersja istniejącej zależności.
- Każda inna zmiana nie pasuje do jednego z poprzednich przypadków.

W przypadku wielu zmian najwyższy element, na który mają wpływ poszczególne zmiany, jest zwiększany, a następujące są resetowane do zera. Na przykład, `MAJOR` gdy jest `MINOR` zwiększany `PATCH` i są resetowane do zera. Gdy `MINOR` jest zwiększany, `PATCH` jest resetowany `MAJOR` do zera, podczas gdy pozostaje nietknięty.

## <a name="version-numbers-in-file-names"></a>Numery wersji w nazwach plików

Pliki pobrane dla .NET Core nosić wersję, na przykład. `dotnet-sdk-2.1.300-win10-x64.exe`

### <a name="preview-versions"></a>Wersje podglądu

Wersje w `-preview[number]-([build]|"final")` wersji zapoznawczej mają dołączoną wersję. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Wersje serwisowe

Po wydaniu wychodzi, gałęzie wydania zazwyczaj przestają produkować codzienne kompilacje i zamiast rozpocząć produkcję kompilacji obsługi. Wersje obsługi `-servicing-[number]` mają dołączoną do wersji. Na przykład `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relacja z wersjami standardu .NET

.NET Standard składa się z zestawu referencyjnego .NET. Istnieje wiele implementacji specyficznych dla każdej platformy. Zestaw odniesienia zawiera definicję interfejsów API .NET, które są częścią danej wersji standardu .NET. Każda implementacja spełnia kontrakt .NET Standard na określonej platformie. Więcej informacji na temat standardu .NET można uzyskać w artykule na temat [standardu .NET](../../standard/net-standard.md) w przewodniku .NET.

Standardowy zestaw referencyjny .NET używa schematu `MAJOR.MINOR` wersji. `PATCH`poziom nie jest przydatne dla .NET Standard, ponieważ udostępnia tylko specyfikację interfejsu API (bez implementacji) i z definicji wszelkie `MINOR` zmiany w interfejsie API będzie reprezentować zmianę w zestawie funkcji, a tym samym nową wersję.

Implementacje na każdej platformie mogą być aktualizowane, zazwyczaj w ramach wersji platformy, a tym samym nie jest oczywiste dla programistów korzystających z .NET Standard na tej platformie.

Każda wersja programu .NET Core implementuje wersję programu .NET Standard. Implementacja wersji programu .NET Standard oznacza obsługę poprzednich wersji programu .NET Standard. .NET Standard i .NET Core niezależnie. To przypadek, że program .NET Core 2.0 implementuje program .NET Standard 2.0. .NET Core 2.1 implementuje również .NET Standard 2.0. Program .NET Core będzie obsługiwać przyszłe wersje programu .NET Standard w miarę ich udostępniania.

| .NET Core | .NET Standard |
|-----------|---------------|
| 1.0       | do 1,6     |
| 2.0       | do 2,0     |
| 2.1       | do 2,0     |
| 2.2       | do 2,0     |
| 3.0       | do 2,1 pkt.     |

## <a name="see-also"></a>Zobacz też

- [Platformy docelowe](../../standard/frameworks.md)
- [Tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md)
- [Arkusz informacyjny cyklu pomocy technicznej .NET](https://dotnet.microsoft.com/platform/support/policy)
- [Powiązanie wersji .NET Core 2+](https://github.com/dotnet/designs/issues/3)
- [Obrazy platformy Docker dla programu .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)
