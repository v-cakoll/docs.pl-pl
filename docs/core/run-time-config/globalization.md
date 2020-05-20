---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 2561e66e6d18cb4036b0719f7e34ea66540fe095
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703125"
---
# <a name="run-time-configuration-options-for-globalization"></a>Opcje konfiguracji czasu wykonywania dla globalizacji

## <a name="invariant-mode"></a>Tryb niezmienny

- Określa, czy aplikacja .NET Core działa w trybie globalizacji-niezmiennym bez dostępu do danych i zachowań specyficznych dla kultury.
- Wartość domyślna: Uruchom aplikację z dostępem do danych kultury ( `false` ).
- Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false`— dostęp do danych kultury<br/>`true`-Uruchom w trybie niezmiennym |
| **Właściwość programu MSBuild** | `InvariantGlobalization` | `false`— dostęp do danych kultury<br/>`true`-Uruchom w trybie niezmiennym |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`— dostęp do danych kultury<br/>`1`-Uruchom w trybie niezmiennym |

### <a name="examples"></a>Przykłady

plik *runtimeconfig. JSON* :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

Plik projektu:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a>Zakresy lat era

- Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też wskazuje, czy daty, które przepełnią zakres dat era <xref:System.ArgumentOutOfRangeException> .
- Domyślne: Sprawdzanie zakresu jest swobodne ( `false` ).
- Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`-swobodne kontrole zakresu<br/>`true`-nadprzepływy powodują wyjątek |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

## <a name="japanese-date-parsing"></a>Japońska analiza daty

- Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".
- Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok ( `false` ).
- Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`-Jest obsługiwana wartość "Gannen" lub "1"<br/>`true`-tylko "1" jest obsługiwana |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

## <a name="japanese-year-format"></a>Japoński rok

- Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.
- Domyślnie: Formatuj pierwszy rok jako "Gannen" ( `false` ).
- Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-Format jako "Gannen"<br/>`true`-formatowanie jako liczba |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

## <a name="nls"></a>NLS

- Określa, czy platforma .NET korzysta z interfejsu API globalizacji języka narodowego (NLS) lub składników międzynarodowych dla aplikacji systemu Windows (ICU). .NET 5,0 i nowsze wersje używają interfejsów API ICU globalizacji domyślnie w systemie Windows 10 maja 2019 Update i nowszych wersjach.
- W przypadku pominięcia tego ustawienia platforma .NET domyślnie używa interfejsów API ICU globalizacji. Jest to równoznaczne z ustawieniem wartości `false` .
- Aby uzyskać więcej informacji, zobacz [interfejsy API globalizacji korzystają z BIBLIOTEK ICU w systemie Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).

| | Nazwa ustawienia | Wartości | Wraca |
| - | - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.UseNls` | `false`-Korzystanie z interfejsów API ICU globalizacji<br/>`true`-Korzystanie z interfejsów API globalizacji NLS | .NET 5,0 |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | `false`-Korzystanie z interfejsów API ICU globalizacji<br/>`true`-Korzystanie z interfejsów API globalizacji NLS | .NET 5,0 |
