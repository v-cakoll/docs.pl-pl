---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 3764d0eb714c094b44ae843a1e626073ff8d82e4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733453"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="a0a2b-103">Opcje konfiguracji czasu wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="a0a2b-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="a0a2b-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="a0a2b-104">Invariant mode</span></span>

- <span data-ttu-id="a0a2b-105">Określa, czy aplikacja .NET Core działa w trybie niezmiennej globalizacji bez dostępu do danych specyficznych dla kultury i zachowań lub czy ma dostęp do danych kultury.</span><span class="sxs-lookup"><span data-stu-id="a0a2b-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="a0a2b-106">Wartość domyślna: Uruchom aplikację z dostępem do danych kultury (`false`).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="a0a2b-107">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="a0a2b-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a0a2b-108">Setting name</span></span> | <span data-ttu-id="a0a2b-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="a0a2b-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0a2b-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="a0a2b-111">`false` dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="a0a2b-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="a0a2b-112">`true` — uruchamianie w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="a0a2b-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a0a2b-113">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="a0a2b-114">`false` dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="a0a2b-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="a0a2b-115">`true` — uruchamianie w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="a0a2b-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="a0a2b-116">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="a0a2b-117">`0` dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="a0a2b-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="a0a2b-118">`1` — uruchamianie w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="a0a2b-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="a0a2b-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a0a2b-119">Examples</span></span>

<span data-ttu-id="a0a2b-120">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="a0a2b-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="a0a2b-121">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a0a2b-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="a0a2b-122">Zakresy lat era</span><span class="sxs-lookup"><span data-stu-id="a0a2b-122">Era year ranges</span></span>

- <span data-ttu-id="a0a2b-123">Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też czy daty, które przepełnią zakres dat ERA, zgłaszają <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="a0a2b-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="a0a2b-124">Domyślne: Sprawdzanie zakresu jest swobodne (`false`).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="a0a2b-125">Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="a0a2b-126">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a0a2b-126">Setting name</span></span> | <span data-ttu-id="a0a2b-127">Wartości</span><span class="sxs-lookup"><span data-stu-id="a0a2b-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0a2b-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="a0a2b-129">kontrole zakresu swobodnego `false`</span><span class="sxs-lookup"><span data-stu-id="a0a2b-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="a0a2b-130">`true` — nadprzepływy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="a0a2b-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="a0a2b-131">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-131">**Environment variable**</span></span> | <span data-ttu-id="a0a2b-132">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-132">N/A</span></span> | <span data-ttu-id="a0a2b-133">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="a0a2b-134">Japońska analiza daty</span><span class="sxs-lookup"><span data-stu-id="a0a2b-134">Japanese date parsing</span></span>

- <span data-ttu-id="a0a2b-135">Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".</span><span class="sxs-lookup"><span data-stu-id="a0a2b-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="a0a2b-136">Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok (`false`).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="a0a2b-137">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a0a2b-138">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a0a2b-138">Setting name</span></span> | <span data-ttu-id="a0a2b-139">Wartości</span><span class="sxs-lookup"><span data-stu-id="a0a2b-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0a2b-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="a0a2b-141">`false` — obsługiwana jest wartość "Gannen" lub "1"</span><span class="sxs-lookup"><span data-stu-id="a0a2b-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="a0a2b-142">Obsługiwane są tylko `true` "1"</span><span class="sxs-lookup"><span data-stu-id="a0a2b-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="a0a2b-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-143">**Environment variable**</span></span> | <span data-ttu-id="a0a2b-144">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-144">N/A</span></span> | <span data-ttu-id="a0a2b-145">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="a0a2b-146">Japoński rok</span><span class="sxs-lookup"><span data-stu-id="a0a2b-146">Japanese year format</span></span>

- <span data-ttu-id="a0a2b-147">Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="a0a2b-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="a0a2b-148">Domyślnie: Formatuj pierwszy rok jako "Gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="a0a2b-149">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="a0a2b-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="a0a2b-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a0a2b-150">Setting name</span></span> | <span data-ttu-id="a0a2b-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="a0a2b-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a0a2b-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="a0a2b-153">`false`-format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="a0a2b-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="a0a2b-154">`true` — formatowanie jako liczba</span><span class="sxs-lookup"><span data-stu-id="a0a2b-154">`true` - format as number</span></span> |
| <span data-ttu-id="a0a2b-155">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a0a2b-155">**Environment variable**</span></span> | <span data-ttu-id="a0a2b-156">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-156">N/A</span></span> | <span data-ttu-id="a0a2b-157">Brak</span><span class="sxs-lookup"><span data-stu-id="a0a2b-157">N/A</span></span> |
