---
title: Domyślna sondowanie — .NET Core
description: Omówienie elementu System. Runtime. Loader. AssemblyLoadContext. default sondowania w celu lokalizowania zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031828"
---
# <a name="default-probing"></a>Domyślna sonda

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> jest odpowiedzialne za lokalizowanie zależności zestawu. W tym artykule opisano logikę sondowania wystąpienia <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType>.

## <a name="host-configured-probing-properties"></a>Host skonfigurował właściwości sondowania

Po uruchomieniu środowiska uruchomieniowego host środowiska uruchomieniowego udostępnia zestaw nazwanych właściwości, które konfigurują <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ścieżki sondowania.

Każda właściwość sondowania jest opcjonalna. Jeśli jest obecny, Każda właściwość jest wartością ciągu, która zawiera rozdzielaną listę ścieżek bezwzględnych. Ogranicznik to ";" w systemie Windows i ":" na wszystkich innych platformach.

|Nazwa właściwości                 |Opis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista ścieżek plików zestawu platformy i aplikacji. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelity. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista ścieżek katalogów do wyszukiwania niezarządzanych (natywnych) bibliotek.        |
|`APP_PATHS`                     | Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych. |
|`APP_NI_PATHS`                  | Lista ścieżek katalogów do wyszukiwania natywnych obrazów zestawów zarządzanych. |

### <a name="how-are-the-properties-populated"></a>Jak są wypełniane właściwości?

Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, czy istnieje plik *\<mojaapl >. deps. JSON* .

- Gdy plik *\*. deps. JSON* jest obecny, jest analizowany w celu wypełnienia właściwości sondowania.
- Gdy plik *\*. deps. JSON* nie istnieje, zakłada się, że katalog aplikacji zawiera wszystkie zależności. Zawartość katalogu służy do wypełniania właściwości sondowania.

Ponadto pliki *\*. deps. JSON* dla wszystkich platform, do których istnieją odwołania, są podobnie analizowane.

Na koniec zmienna środowiskowa `ADDITIONAL_DEPS` może służyć do dodawania dodatkowych zależności.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Jak mogę wyświetlić właściwości sondowania z kodu zarządzanego?

Każda właściwość jest dostępna przez wywołanie funkcji <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> z nazwą właściwości z powyższej tabeli.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Jak mogę debugować konstrukcję właściwości sondowania?

Host środowiska uruchomieniowego platformy .NET Core będzie wyprowadzać przydatne komunikaty śledzenia, gdy są włączone pewne zmienne środowiskowe:

|Zmienna środowiskowa        |Opis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Włącza śledzenie.|
|`COREHOST_TRACEFILE=<path>` |Śladuje do ścieżki pliku zamiast domyślnego `stderr`.|
|`COREHOST_TRACE_VERBOSITY`  |Ustawia poziom szczegółowości od 1 (najniższy) do 4 (najwyższy).|

## <a name="managed-assembly-default-probing"></a>Domyślna sondowanie zestawu zarządzanego

Podczas sondowania w celu zlokalizowania zestawu zarządzanego <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> wygląda następująco:

- Pliki pasujące do <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> w `TRUSTED_PLATFORM_ASSEMBLIES` (po usunięciu rozszerzeń plików).
- Pliki zestawu obrazów natywnych w `APP_NI_PATHS` z typowymi rozszerzeniami plików.
- Pliki zestawów w `APP_PATHS` ze wspólnymi rozszerzeniami plików.

## <a name="satellite-resource-assembly-probing"></a>Sonda zestawu (zasobów) dla satelity

Aby znaleźć zestaw satelicki dla określonej kultury, należy utworzyć zestaw ścieżek plików.

Dla każdej ścieżki w `PLATFORM_RESOURCE_ROOTS`, a następnie `APP_PATHS`, dołącz ciąg <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType>, separator katalogu, ciąg <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> i rozszerzenie ". dll".

Jeśli istnieje odpowiedni plik, spróbuj załadować i zwrócić go.

## <a name="unmanaged-native-library-probing"></a>Badanie biblioteki niezarządzanej (natywnej)

Podczas sondowania w celu zlokalizowania biblioteki niezarządzanej `NATIVE_DLL_SEARCH_DIRECTORIES` są przeszukiwane w poszukiwaniu zgodnej biblioteki.
