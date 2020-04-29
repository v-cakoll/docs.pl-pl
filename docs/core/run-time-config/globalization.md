---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 7668c345181d7c08cfca9c5cb76b8addd76223ec
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506808"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="6a177-103">Opcje konfiguracji czasu wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="6a177-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="6a177-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="6a177-104">Invariant mode</span></span>

- <span data-ttu-id="6a177-105">Określa, czy aplikacja .NET Core działa w trybie globalizacji-niezmiennym bez dostępu do danych i zachowań specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="6a177-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="6a177-106">Wartość domyślna: Uruchom aplikację z dostępem do danych kultury (`false`).</span><span class="sxs-lookup"><span data-stu-id="6a177-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="6a177-107">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="6a177-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="6a177-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="6a177-108">Setting name</span></span> | <span data-ttu-id="6a177-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="6a177-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a177-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a177-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="6a177-111">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="6a177-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="6a177-112">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="6a177-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="6a177-113">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="6a177-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="6a177-114">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="6a177-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="6a177-115">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="6a177-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="6a177-116">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="6a177-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="6a177-117">`0`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="6a177-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="6a177-118">`1`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="6a177-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="6a177-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6a177-119">Examples</span></span>

<span data-ttu-id="6a177-120">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="6a177-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="6a177-121">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="6a177-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="6a177-122">Zakresy lat era</span><span class="sxs-lookup"><span data-stu-id="6a177-122">Era year ranges</span></span>

- <span data-ttu-id="6a177-123">Określa, <xref:System.ArgumentOutOfRangeException>czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też wskazuje, czy daty, które przepełnią zakres dat ERA.</span><span class="sxs-lookup"><span data-stu-id="6a177-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="6a177-124">Domyślne: Sprawdzanie zakresu jest swobodne`false`().</span><span class="sxs-lookup"><span data-stu-id="6a177-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="6a177-125">Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="6a177-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="6a177-126">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="6a177-126">Setting name</span></span> | <span data-ttu-id="6a177-127">Wartości</span><span class="sxs-lookup"><span data-stu-id="6a177-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a177-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a177-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="6a177-129">`false`-swobodne kontrole zakresu</span><span class="sxs-lookup"><span data-stu-id="6a177-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="6a177-130">`true`-nadprzepływy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="6a177-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="6a177-131">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="6a177-131">**Environment variable**</span></span> | <span data-ttu-id="6a177-132">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-132">N/A</span></span> | <span data-ttu-id="6a177-133">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="6a177-134">Japońska analiza daty</span><span class="sxs-lookup"><span data-stu-id="6a177-134">Japanese date parsing</span></span>

- <span data-ttu-id="6a177-135">Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".</span><span class="sxs-lookup"><span data-stu-id="6a177-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="6a177-136">Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok (`false`).</span><span class="sxs-lookup"><span data-stu-id="6a177-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="6a177-137">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="6a177-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="6a177-138">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="6a177-138">Setting name</span></span> | <span data-ttu-id="6a177-139">Wartości</span><span class="sxs-lookup"><span data-stu-id="6a177-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a177-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a177-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="6a177-141">`false`-Jest obsługiwana wartość "Gannen" lub "1"</span><span class="sxs-lookup"><span data-stu-id="6a177-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="6a177-142">`true`-tylko "1" jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="6a177-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="6a177-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="6a177-143">**Environment variable**</span></span> | <span data-ttu-id="6a177-144">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-144">N/A</span></span> | <span data-ttu-id="6a177-145">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="6a177-146">Japoński rok</span><span class="sxs-lookup"><span data-stu-id="6a177-146">Japanese year format</span></span>

- <span data-ttu-id="6a177-147">Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="6a177-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="6a177-148">Domyślnie: Formatuj pierwszy rok jako "Gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="6a177-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="6a177-149">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="6a177-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="6a177-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="6a177-150">Setting name</span></span> | <span data-ttu-id="6a177-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="6a177-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="6a177-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="6a177-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="6a177-153">`false`-Format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="6a177-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="6a177-154">`true`-formatowanie jako liczba</span><span class="sxs-lookup"><span data-stu-id="6a177-154">`true` - format as number</span></span> |
| <span data-ttu-id="6a177-155">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="6a177-155">**Environment variable**</span></span> | <span data-ttu-id="6a177-156">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-156">N/A</span></span> | <span data-ttu-id="6a177-157">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="6a177-157">N/A</span></span> |
