---
title: Domyślna sondowanie — .NET Core
description: Omówienie logiki sondowania platformy <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> .NET Core do lokalizowania zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 2fa8a13bcb08a767fa965621f95bec8619aea5cc
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926406"
---
# <a name="default-probing"></a>Domyślna sonda

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Wystąpienie jest odpowiedzialne za lokalizowanie zależności zestawu. W <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tym artykule opisano logikę sondowania wystąpienia.

## <a name="host-configured-probing-properties"></a>Host skonfigurował właściwości sondowania

Po uruchomieniu środowiska uruchomieniowego host środowiska uruchomieniowego udostępnia zestaw nazwanych właściwości, które konfigurują <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ścieżki sondy.

Każda właściwość sondowania jest opcjonalna.  Jeśli jest obecny, Każda właściwość jest wartością ciągu, która zawiera rozdzielaną listę ścieżek bezwzględnych. Ogranicznik to ";" w systemie Windows i ":" na wszystkich innych platformach.

|Nazwa właściwości                 |Opis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista ścieżek plików zestawu platformy i aplikacji. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelity. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista ścieżek katalogów do wyszukiwania niezarządzanych (natywnych) bibliotek.        |
|`APP_PATHS`                     | Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych |
|`APP_NI_PATHS`                  | Lista ścieżek katalogów do wyszukiwania natywnych obrazów zestawów zarządzanych. |

### <a name="how-are-the-properties-populated"></a>Jak są wypełniane właściwości?

Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, `<myapp>.deps.json` czy plik istnieje.

- `*.deps.json` Gdy plik jest obecny, jest analizowany w celu wypełnienia właściwości sondowania.
- `*.deps.json` Gdy plik nie jest obecny, zakłada się, że katalog aplikacji zawiera wszystkie zależności. Zawartość katalogu służy do wypełniania właściwości sondowania.

Ponadto pliki dla `*.deps.json` dowolnych platform, do których istnieją odwołania, są podobnie analizowane.

Na koniec zmienna `ADDITIONAL_DEPS` środowiskowa może służyć do dodawania dodatkowych zależności.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Jak mogę wyświetlić właściwości sondowania z kodu zarządzanego?

Każda właściwość jest dostępna przez wywołanie <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> funkcji z nazwą właściwości z powyższej tabeli.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Jak mogę debugować konstrukcję właściwości sondowania?

Host środowiska uruchomieniowego platformy .NET Core będzie wyprowadzać przydatne komunikaty śledzenia, gdy są włączone pewne zmienne środowiskowe:

|Zmienna środowiskowa        |Opis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Włącza śledzenie.|
|`COREHOST_TRACEFILE=<path>` |Ślady do ścieżki pliku zamiast wartości domyślnej `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Ustawia poziom szczegółowości od 1 (najniższy) do 4 (najwyższy).|

## <a name="managed-assembly-default-probing"></a>Domyślna sondowanie zestawu zarządzanego

Podczas sondowania w celu zlokalizowania zestawu <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zarządzanego wygląd wygląda następująco:

- Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do `TRUSTED_PLATFORM_ASSEMBLIES` programu (po usunięciu rozszerzeń plików).
- Pliki zestawu obrazów natywnych `APP_NI_PATHS` w programie ze wspólnymi rozszerzeniami plików.
- Pliki zestawów w `APP_PATHS` programie ze wspólnymi rozszerzeniami plików.

## <a name="satellite-resource-assembly-probing"></a>Sonda zestawu (zasobów) dla satelity

Aby znaleźć zestaw satelicki dla określonej kultury, należy utworzyć zestaw ścieżek plików.

Dla każdej ścieżki w `PLATFORM_RESOURCE_ROOTS` , a `APP_PATHS`następnie Dołącz <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie ". dll".

Jeśli istnieje odpowiedni plik, spróbuj załadować i zwrócić go.

## <a name="unmanaged-native-library-probing"></a>Badanie biblioteki niezarządzanej (natywnej)

Podczas sondowania w celu zlokalizowania biblioteki `NATIVE_DLL_SEARCH_DIRECTORIES` niezarządzanej są one przeszukiwane w poszukiwaniu zgodnej biblioteki.
