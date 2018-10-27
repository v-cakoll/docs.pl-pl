---
title: Przechowywanie wersji platformy .NET core
description: Dowiedz się, jak działa wersji platformy .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 07/26/2018
ms.openlocfilehash: 9f77709abf59d5346bf5e3c6f512cfabbf9e50de
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188472"
---
# <a name="net-core-versioning"></a>Przechowywanie wersji platformy .NET core

.NET core odnosi się do środowiska uruchomieniowego programu .NET Core i .NET Core SDK, który zawiera narzędzia potrzebne do tworzenia aplikacji. Zestawów .NET core SDK są przeznaczone do pracy z poprzednich wersji środowiska uruchomieniowego programu .NET Core. W tym artykule wyjaśniono, środowisko uruchomieniowe i strategii wersji zestawu SDK. Wyjaśnienie numery wersji dla platformy .NET Standard można znaleźć w artykule Przedstawiamy [.NET Standard](../../standard/net-standard.md#net-implementation-support).

Środowisko uruchomieniowe programu .NET Core i .NET Core SDK dodania nowych funkcji w różnych stawki — ogólnie rzecz biorąc .NET Core SDK zawiera szybko zaktualizować narzędzia więcej niż środowisko uruchomieniowe programu .NET Core zmiany środowiska uruchomieniowego, którego używasz w środowisku produkcyjnym. Niestety ten problem, przyniosło kilka strategii przechowywania wersji w ciągu kilku ostatnich lat. Informacje na temat historii w artykule na [wersji platformy .NET Core](version-history.md).

## <a name="versioning-details"></a>Szczegóły wersji

".NET Core 2.1" odnosi się do numer wersji środowiska uruchomieniowego programu .NET Core. Środowisko uruchomieniowe programu .NET Core zawiera główny/drobnych/patch sposobem przechowywania wersji, który następuje po [wersji semantycznej](#semantic-versioning).

.NET Core SDK nie postępuj zgodnie z semantyki przechowywania wersji. .NET Core SDK zwalnia szybciej, a jego wersji muszą komunikować się wyrównany środowiska uruchomieniowego i zestawu SDK własnych niewielkie i poprawki wersji. Pierwsze dwa stanowiska wersji zestawu .NET Core SDK są zablokowane do środowiska uruchomieniowego .NET Core ona udostępniona. Każda wersja zestawu SDK można tworzyć aplikacje, dla tego środowiska uruchomieniowego lub dowolnej starszej wersji.

Trzeci położenie numer wersji zestawu SDK komunikuje się oba pomocnicze i poprawianie numer. Wersja pomocnicza jest pomnożona przez 100. Podrzędny numer wersji 1, poprawki w wersji 2 jest przedstawiany jako 102. Dwie cyfry końcowe reprezentują numer poprawki. Wersja platformy .NET Core 2.2 może na przykład utworzyć wersji, takich jak Poniższa:

| Zmiana                | Środowisko uruchomieniowe programu .NET core | .NET core SDK (*) |
|-----------------------|-------------------|-------------------|
| Wersja początkowa       | 2.2.0             | 2.2.100           |
| Poprawka zestawu SDK             | 2.2.0             | 2.2.101           |
| Środowisko uruchomieniowe i zestaw SDK poprawki | 2.2.1             | 2.2.102           |
| Zmiana funkcji zestawu SDK    | 2.2.1             | 2.2.200           |

(\*) Ten wykres używa przyszłych 2.2 środowisko uruchomieniowe programu .NET Core co w przykładzie, ponieważ historyczne artefaktu przeznaczone pierwszy zestaw SDK dla platformy .NET Core 2.1 jest 2.1.300. Aby uzyskać więcej informacji, zobacz [historię wersji platformy .NET Core](version-history.md).

UWAGI:

* Jeśli zestaw SDK zawiera 10 aktualizacje funkcji przed aktualizacją funkcji środowiska uruchomieniowego, numery wersji przejdą do serii 1000 z międzynarodowymi numerami identyfikującymi takich jak 2.2.1000 jako wydawanie funkcji od 2.2.900. Ta sytuacja nie jest wystąpienie jest oczekiwane.
* 99 poprawkami wydań, bez wydawania funkcji nie zostanie wykonana. Jeśli ten numer zbliża się do wydania, wymusza wersji funkcji.

Można zobaczyć więcej szczegółów, w początkowej wniosek na [dotnet/projekty](https://github.com/dotnet/designs/pull/29) repozytorium.

## <a name="semantic-versioning"></a>Przechowywanie wersji semantyczne

.NET Core *środowiska uruchomieniowego* około działa zgodnie z [Semantic Versioning (SemVer)](https://semver.org/), przyjęcie użytkowania `MAJOR.MINOR.PATCH` przechowywania wersji, użycie różnych części numeru wersji w celu opisania stopnia i typ Zmiana.

```
MAJOR.MINOR.PATCH[-PRERELEASE-BUILDNUMBER]
```

Opcjonalny `PRERELEASE` i `BUILDNUMBER` części nigdy nie są częścią obsługiwanych wersji i istnieją tylko na nocnych kompilacji, lokalne kompilacje z celów źródła i nieobsługiwane wersje zapoznawcze.

### <a name="understand-runtime-version-number-changes"></a>Omówienie zmiany numeru wersji środowiska uruchomieniowego

`MAJOR` jest zwiększany, gdy:

* Znaczących zmianach produkt lub nowym kierunku produktu.
* Powodująca niezgodność zmiany zostały pobrane. Istnieje wysoka pasek z zaakceptowania zmian powodujących niezgodność.
* Stara wersja nie jest już obsługiwana.
* Nowsze `MAJOR` przyjmuje się wersja istniejące zależności.

`MINOR` jest zwiększany, gdy:

* Publiczny obszar powierzchni interfejsu API jest dodawany.
* Nowe zachowanie jest dodawany.
* Nowsze `MINOR` przyjmuje się wersja istniejące zależności.
* Wprowadzono nowe zależności.

`PATCH` jest zwiększany, gdy:

* Poprawki zostały wprowadzone.
* Zostanie dodana jego obsługa dla nowszej platformy.
* Nowsze `PATCH` przyjmuje się wersja istniejące zależności.
* Inne zmiany nie mieści się jednego z poprzednich przypadków.

W przypadku wielu zmian najwyższy element wpływ poszczególnych zmian jest zwiększany, a poniższych jest resetowany do zera. Na przykład, gdy `MAJOR` jest zwiększany `MINOR` i `PATCH` jest resetowany do zera. Gdy `MINOR` jest zwiększany `PATCH` jest resetowany do zera trochę `MAJOR` nie została zmieniona po lewej.

## <a name="version-numbers-in-file-names"></a>Numery wersji w nazwach plików

Pliki pobierane dla platformy .NET Core przeniesienia wersji, na przykład `dotnet-sdk-2.1.300-win10-x64.exe`.

### <a name="preview-versions"></a>Wersje (wersja zapoznawcza)

Wersji zapoznawczych mają `-preview[number]-([build]|"final")` dołączany do wersji. Na przykład `2.0.0-preview1-final`.

### <a name="servicing-versions"></a>Obsługa wersji

Po wydaniu trafia, gałęzie wydań jest ogólnie Zatrzymaj tworzenie codzienne kompilacje i zamiast tego zaczniesz tworzenie obsługi kompilacji. Wersje obsługi mają `-servicing-[number]` dołączany do wersji. Na przykład `2.0.1-servicing-006924`.

## <a name="relationship-to-net-standard-versions"></a>Relacja do wersji .NET Standard

.NET standard składa się z zestawu odwołania platformy .NET. Wiele implementacji są specyficzne dla poszczególnych platform. Zestaw odwołania zawiera definicji interfejsów API platformy .NET, które są dostępne w ramach danej wersji .NET Standard. Każda implementacja spełnia .NET Standard kontraktu na danej platformie. Można znaleźć więcej informacji na temat .NET Standard w artykule na [.NET Standard](../../standard/net-standard.md) w przewodniku programu .NET.

.NET Standard używa zestawu odwołania `MAJOR.MINOR` schematu przechowywania wersji. `PATCH` poziom nie jest przydatne dla platformy .NET Standard, ponieważ udostępnia tylko specyfikację interfejsu API (nie implementacji), a następnie zgodnie z definicją wszelkie zmiany interfejsu API reprezentuje zmianę zestawu funkcji i dlatego nową `MINOR` wersji.

Implementacje na każdej z platform mogą być aktualizowane, zazwyczaj w ramach wersji platformy i w związku z tym nie oczywisty dla programistów przy użyciu platformy .NET Standard na tej platformie.

Każda wersja programu .NET Core implementuje wersji programu .NET Standard. Zaimplementowanie wersji .NET Standard oznacza pomocy technicznej dla wcześniejszych wersji programu .NET Standard. Wersja platformy .NET standard i .NET Core niezależnie. Jest zbieżność, że zestaw .NET Core 2.0 implementuje .NET Standard 2.0. .NET core 2.1 implementuje również .NET Standard 2.0. .NET core będzie obsługiwać przyszłych wersjach programu .NET Standard, gdy tylko zostaną udostępnione.

| .NET Core | .NET standard |
|-----------|---------------|
| 1.0       | do wersji 1.6     |
| 2.0       | do 2,0     |
| 2.1       | do 2,0     |

## <a name="see-also"></a>Zobacz także

* [Platformy docelowe](../../standard/frameworks.md)  
* [Tworzenie pakietów dystrybucji platformy .NET Core](../build/distribution-packaging.md)  
* [.NET core pomocy technicznej cyklu życia faktu arkusza](https://www.microsoft.com/net/core/support)  
* [Wiązanie wersji programu .NET core 2 +](https://github.com/dotnet/designs/issues/3)  
* [Obrazy platformy docker dla platformy .NET Core](https://hub.docker.com/r/microsoft/dotnet/)
