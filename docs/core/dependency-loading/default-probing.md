---
title: Sondowanie domyślne — .NET Core
description: Omówienie .NET Core's System.Runtime.Loader.AssemblyLoadContext.Default sondowania logiki, aby zlokalizować zależności.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 500ee6ee863b1f311970a9e718936f57f7d4efd6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399092"
---
# <a name="default-probing"></a>Sondowanie domyślne

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> jest odpowiedzialny za lokalizowanie zależności zestawu. W tym <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> artykule opisano logikę sondowania wystąpienia.

## <a name="host-configured-probing-properties"></a>Host skonfigurowane właściwości sondowania

Po uruchomieniu czasu uruchomieniowego host akcesoryjna udostępnia <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zestaw nazwanych właściwości sondowania, które konfigurują ścieżki sondowania.

Każda właściwość sondowania jest opcjonalna. Jeśli jest obecny, każda właściwość jest wartością ciągu, która zawiera rozdzieloną listę ścieżek bezwzględnych. Ogranicznik jest ';' w systemie Windows i ':' na wszystkich innych platformach.

|Nazwa właściwości                 |Opis  |
|------------------------------|---------|
|`TRUSTED_PLATFORM_ASSEMBLIES`   | Lista ścieżek plików zestawów platform i aplikacji. |
|`PLATFORM_RESOURCE_ROOTS`       | Lista ścieżek katalogów do wyszukiwania zestawów zasobów satelitarnych. |
|`NATIVE_DLL_SEARCH_DIRECTORIES` | Lista ścieżek katalogów do wyszukiwania bibliotek niezarządzanych (natywnych).        |
|`APP_PATHS`                     | Lista ścieżek katalogów do wyszukiwania zestawów zarządzanych. |
|`APP_NI_PATHS`                  | Lista ścieżek katalogów do wyszukiwania obrazów macierzystych zestawów zarządzanych. |

### <a name="how-are-the-properties-populated"></a>Jak są wypełniane właściwości?

Istnieją dwa główne scenariusze wypełniania właściwości w zależności od tego, czy istnieje plik * \<myapp>.deps.json.*

- Gdy plik * \*.deps.json* jest obecny, jest analizowany, aby wypełnić właściwości sondowania.
- Gdy plik * \*.deps.json* nie jest obecny, przyjmuje się, że katalog aplikacji zawiera wszystkie zależności. Zawartość katalogu służy do wypełniania właściwości sondowania.

Ponadto pliki * \*.deps.json* dla wszelkich struktur, do których istnieje odwołanie, są podobnie analizowane.

Na koniec `ADDITIONAL_DEPS` zmienna środowiskowa może służyć do dodawania dodatkowych zależności.

### <a name="how-do-i-see-the-probing-properties-from-managed-code"></a>Jak wyświetlić właściwości sondowania z kodu zarządzanego?

Każda właściwość jest dostępna <xref:System.AppContext.GetData(System.String)?displayProperty=nameWithType> przez wywołanie funkcji z nazwą właściwości z powyższej tabeli.

### <a name="how-do-i-debug-the-probing-properties-construction"></a>Jak debugować konstrukcję właściwości sondowania?

Host środowiska uruchomieniowego .NET Core wygeneruje przydatne komunikaty śledzenia, gdy pewne zmienne środowiskowe są włączone:

|Zmienna środowiskowa        |Opis  |
|----------------------------|---------|
|`COREHOST_TRACE=1`          |Umożliwia śledzenie.|
|`COREHOST_TRACEFILE=<path>` |Ślady do ścieżki pliku zamiast `stderr`domyślnej .|
|`COREHOST_TRACE_VERBOSITY`  |Ustawia szczegółowość od 1 (najniższa) do 4 (najwyższa).|

## <a name="managed-assembly-default-probing"></a>Domyślne sondowanie zestawu zarządzanego

Podczas sondowania w celu zlokalizowania zarządzanego <xref:System.Runtime.Loader.AssemblyLoadContext.Default%2A?displayProperty=nameWithType> zestawu, wygląda w kolejności na:

- Pliki pasujące <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> `TRUSTED_PLATFORM_ASSEMBLIES` do in (po usunięciu rozszerzeń plików).
- Pliki natywnego zestawu obrazów `APP_NI_PATHS` ze wspólnymi rozszerzeniami plików.
- Pliki zestawów `APP_PATHS` ze wspólnymi rozszerzeniami plików.

## <a name="satellite-resource-assembly-probing"></a>Sondowanie zestawu satelitarnego (zasobu)

Aby znaleźć zestaw satelicki dla określonej kultury, skonstruować zestaw ścieżek plików.

Dla każdej `PLATFORM_RESOURCE_ROOTS` ścieżki `APP_PATHS`w i <xref:System.Globalization.CultureInfo.Name?displayProperty=nameWithType> następnie dołączaciąg, separator katalogu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> ciąg i rozszerzenie '.dll'.

Jeśli istnieje dowolny pasujący plik, spróbuj go załadować i zwrócić.

## <a name="unmanaged-native-library-probing"></a>Sondowanie biblioteki niezarządzanej (natywnej)

Podczas sondowania w celu zlokalizowania `NATIVE_DLL_SEARCH_DIRECTORIES` biblioteki niezarządzanej przeszukiwane są wyszukiwane w poszukiwaniu pasującej biblioteki.
