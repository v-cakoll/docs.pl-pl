---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0571c64eff5b38aafa37026fb2ba7f4aef778beb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802779"
---
# <a name="run-time-configuration-options-for-globalization"></a>Opcje konfiguracji czasu wykonywania dla globalizacji

## <a name="invariant-mode"></a>Tryb niezmienny

- Określa, czy aplikacja .NET Core działa w trybie niezmiennej globalizacji bez dostępu do danych specyficznych dla kultury i zachowań lub czy ma dostęp do danych kultury.
- Wartość domyślna: Uruchom aplikację z dostępem do danych kultury (`false`).
- Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/globalization-invariant-mode.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `System.Globalization.Invariant` | `false` dostęp do danych kultury<br/>`true` — uruchamianie w trybie niezmiennym |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0` dostęp do danych kultury<br/>`1` — uruchamianie w trybie niezmiennym |

## <a name="era-year-ranges"></a>Zakresy lat era

- Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też czy daty, które przepełnią zakres dat ERA, zgłaszają <xref:System.ArgumentOutOfRangeException>.
- Domyślne: Sprawdzanie zakresu jest swobodne (`false`).
- Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | kontrole zakresu swobodnego `false`<br/>`true` — nadprzepływy powodują wyjątek |
| **Zmienna środowiskowa** | N/D | N/D |

## <a name="japanese-date-parsing"></a>Japońska analiza daty

- Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".
- Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok (`false`).
- Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false` — obsługiwana jest wartość "Gannen" lub "1"<br/>Obsługiwane są tylko `true` "1" |
| **Zmienna środowiskowa** | N/D | N/D |

## <a name="japanese-year-format"></a>Japoński rok

- Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.
- Domyślnie: Formatuj pierwszy rok jako "Gannen" (`false`).
- Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig. JSON** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`-format jako "Gannen"<br/>`true` — formatowanie jako liczba |
| **Zmienna środowiskowa** | N/D | N/D |
