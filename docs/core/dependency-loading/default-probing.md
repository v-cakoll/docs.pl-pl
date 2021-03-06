---
title: Domyślna sondowanie — .NET Core
description: Omówienie elementu System. Runtime. Loader. AssemblyLoadContext. default sondowania w celu lokalizowania zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 1e347c716c2d739a1bd03be056b57fdbda6c678f
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859513"
---
# <a name="default-probing"></a>Domyślna sonda

<xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> Wystąpienie jest odpowiedzialne za lokalizowanie zależności zestawu. W <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> tym artykule opisano logikę sondowania wystąpienia.

## <a name="host-configured-probing-properties"></a>Host skonfigurował właściwości sondowania

Po uruchomieniu środowiska uruchomieniowego host środowiska uruchomieniowego udostępnia zestaw nazwanych właściwości, które konfigurują <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> ścieżki sondy.

Każda właściwość sondowania jest opcjonalna. Jeśli jest obecny, Każda właściwość jest wartością ciągu, która zawiera rozdzielaną listę ścieżek bezwzględnych. Ogranicznik to ";" w systemie Windows i ":" na wszystkich innych platformach.

|Nazwa właściwości                 |Opis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista ścieżek plików zestawu platformy i aplikacji. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelity. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista ścieżek katalogów do wyszukiwania niezarządzanych (natywnych) bibliotek.        |
|`APP_PATHS`                     | Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych. |
|`APP_NI_PATHS`                  | Lista ścieżek katalogów do wyszukiwania natywnych obrazów zestawów zarządzanych. |

### <a name="how-are-the-properties-populated"></a>Jak są wypełniane właściwości?

Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, * \<czy istnieje plik MojaApl>. deps. JSON* .

- Gdy plik * \*. deps. JSON* jest obecny, jest analizowany w celu wypełnienia właściwości sondowania.
- Gdy plik * \*. deps. JSON* nie istnieje, zakłada się, że katalog aplikacji zawiera wszystkie zależności. Zawartość katalogu służy do wypełniania właściwości sondowania.

Ponadto pliki * \*. deps. JSON* dla wszystkich platform, do których istnieją odwołania, są podobnie analizowane.

Na koniec zmienna `ADDITIONAL_DEPS` środowiskowa może służyć do dodawania dodatkowych zależności.

Właściwości `APP_PATHS` i `APP_NI_PATHS` nie są domyślnie wypełniane i pomijane w przypadku większości aplikacji.

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

Podczas sondowania w celu zlokalizowania zestawu zarządzanego <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> wygląd wygląda następująco:

- Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do `TRUSTED_PLATFORM_ASSEMBLIES` programu (po usunięciu rozszerzeń plików).
- Pliki zestawu obrazów natywnych `APP_NI_PATHS` w programie ze wspólnymi rozszerzeniami plików.
- Pliki zestawów w `APP_PATHS` programie ze wspólnymi rozszerzeniami plików.

## <a name="satellite-resource-assembly-probing"></a>Sonda zestawu (zasobów) dla satelity

Aby znaleźć zestaw satelicki dla określonej kultury, należy utworzyć zestaw ścieżek plików.

Dla każdej ścieżki w `PLATFORM_RESOURCE_ROOTS` , a `APP_PATHS`następnie Dołącz <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> ciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie ". dll".

Jeśli istnieje odpowiedni plik, spróbuj załadować i zwrócić go.

## <a name="unmanaged-native-library-probing"></a>Badanie biblioteki niezarządzanej (natywnej)

Podczas sondowania w celu zlokalizowania biblioteki niezarządzanej `NATIVE_DLL_SEARCH_DIRECTORIES` są one przeszukiwane w poszukiwaniu zgodnej biblioteki.
