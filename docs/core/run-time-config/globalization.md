---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach w czasie wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład o tym, jak analizuje daty japońskie.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733453"
---
# <a name="run-time-configuration-options-for-globalization"></a>Opcje konfiguracji w czasie wykonywania dla globalizacji

## <a name="invariant-mode"></a>Tryb niezmienny

- Określa, czy aplikacja .NET Core działa w trybie niewariantnym globalizacji bez dostępu do danych i zachowania specyficznych dla kultury, czy też ma dostęp do danych kulturowych.
- Domyślnie: uruchom aplikację z dostępem do danych kulturowych (`false`).
- Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `System.Globalization.Invariant` | `false`- dostęp do danych dotyczących kultury<br/>`true`- uruchomić w trybie niezmiennym |
| **MSBuild, właściwość** | `InvariantGlobalization` | `false`- dostęp do danych dotyczących kultury<br/>`true`- uruchomić w trybie niezmiennym |
| **Zmienna środowiskowa** | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | `0`- dostęp do danych dotyczących kultury<br/>`1`- uruchomić w trybie niezmiennym |

### <a name="examples"></a>Przykłady

*plik runtimeconfig.json:*

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

## <a name="era-year-ranges"></a>Zakresy roku era

- Określa, czy kontrole zakresu dla kalendarzy obsługujących wiele epok są złagodzone, <xref:System.ArgumentOutOfRangeException>czy daty przepełniające zakres dat ery wyrzucające .
- Domyślnie: Kontrole zakresu`false`są złagodzone ( ).
- Aby uzyskać więcej informacji, zobacz [Kalendarze, eby i zakresy dat: kontrole zakresu złagodzonego](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | `false`- rozluźnione kontrole zasięgu<br/>`true`- przelewy powodują wyjątek |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

## <a name="japanese-date-parsing"></a>Japońskie analizowanie dat

- Określa, czy ciąg zawierający "1" lub "Gannen" jako rok analizuje pomyślnie lub czy tylko "1" jest obsługiwana.
- Domyślnie: Parse ciągi, które zawierają "1" lub`false`"Gannen" jako rok ( ).
- Aby uzyskać więcej informacji, zobacz [Reprezentowanie dat w kalendarzach z wieloma epokami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | `false`- "Gannen" lub "1" jest obsługiwany<br/>`true`- obsługiwane jest tylko "1" |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |

## <a name="japanese-year-format"></a>Japoński format roku

- Określa, czy pierwszy rok ery kalendarza japońskiego jest sformatowany jako "Gannen" czy jako liczba.
- Domyślnie: Formatuj pierwszy rok`false`jako "Gannen" ( ).
- Aby uzyskać więcej informacji, zobacz [Reprezentowanie dat w kalendarzach z wieloma epokami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).

| | Nazwa ustawienia | Wartości |
| - | - | - |
| **runtimeconfig.json** | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | `false`- format jako "Gannen"<br/>`true`- format jako liczba |
| **Zmienna środowiskowa** | Nie dotyczy | Nie dotyczy |
