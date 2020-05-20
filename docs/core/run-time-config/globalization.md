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
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="3af8b-103">Opcje konfiguracji czasu wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="3af8b-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="3af8b-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="3af8b-104">Invariant mode</span></span>

- <span data-ttu-id="3af8b-105">Określa, czy aplikacja .NET Core działa w trybie globalizacji-niezmiennym bez dostępu do danych i zachowań specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="3af8b-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="3af8b-106">Wartość domyślna: Uruchom aplikację z dostępem do danych kultury ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="3af8b-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="3af8b-107">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="3af8b-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="3af8b-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="3af8b-108">Setting name</span></span> | <span data-ttu-id="3af8b-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="3af8b-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3af8b-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3af8b-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="3af8b-111">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="3af8b-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="3af8b-112">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="3af8b-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="3af8b-113">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="3af8b-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="3af8b-114">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="3af8b-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="3af8b-115">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="3af8b-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="3af8b-116">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="3af8b-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="3af8b-117">`0`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="3af8b-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="3af8b-118">`1`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="3af8b-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="3af8b-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3af8b-119">Examples</span></span>

<span data-ttu-id="3af8b-120">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="3af8b-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="3af8b-121">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="3af8b-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="3af8b-122">Zakresy lat era</span><span class="sxs-lookup"><span data-stu-id="3af8b-122">Era year ranges</span></span>

- <span data-ttu-id="3af8b-123">Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też wskazuje, czy daty, które przepełnią zakres dat era <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="3af8b-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="3af8b-124">Domyślne: Sprawdzanie zakresu jest swobodne ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="3af8b-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="3af8b-125">Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="3af8b-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="3af8b-126">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="3af8b-126">Setting name</span></span> | <span data-ttu-id="3af8b-127">Wartości</span><span class="sxs-lookup"><span data-stu-id="3af8b-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3af8b-128">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3af8b-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="3af8b-129">`false`-swobodne kontrole zakresu</span><span class="sxs-lookup"><span data-stu-id="3af8b-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="3af8b-130">`true`-nadprzepływy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="3af8b-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="3af8b-131">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="3af8b-131">**Environment variable**</span></span> | <span data-ttu-id="3af8b-132">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-132">N/A</span></span> | <span data-ttu-id="3af8b-133">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="3af8b-134">Japońska analiza daty</span><span class="sxs-lookup"><span data-stu-id="3af8b-134">Japanese date parsing</span></span>

- <span data-ttu-id="3af8b-135">Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".</span><span class="sxs-lookup"><span data-stu-id="3af8b-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="3af8b-136">Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="3af8b-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="3af8b-137">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="3af8b-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="3af8b-138">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="3af8b-138">Setting name</span></span> | <span data-ttu-id="3af8b-139">Wartości</span><span class="sxs-lookup"><span data-stu-id="3af8b-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3af8b-140">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3af8b-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="3af8b-141">`false`-Jest obsługiwana wartość "Gannen" lub "1"</span><span class="sxs-lookup"><span data-stu-id="3af8b-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="3af8b-142">`true`-tylko "1" jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="3af8b-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="3af8b-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="3af8b-143">**Environment variable**</span></span> | <span data-ttu-id="3af8b-144">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-144">N/A</span></span> | <span data-ttu-id="3af8b-145">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="3af8b-146">Japoński rok</span><span class="sxs-lookup"><span data-stu-id="3af8b-146">Japanese year format</span></span>

- <span data-ttu-id="3af8b-147">Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="3af8b-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="3af8b-148">Domyślnie: Formatuj pierwszy rok jako "Gannen" ( `false` ).</span><span class="sxs-lookup"><span data-stu-id="3af8b-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="3af8b-149">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="3af8b-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="3af8b-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="3af8b-150">Setting name</span></span> | <span data-ttu-id="3af8b-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="3af8b-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3af8b-152">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3af8b-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="3af8b-153">`false`-Format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="3af8b-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="3af8b-154">`true`-formatowanie jako liczba</span><span class="sxs-lookup"><span data-stu-id="3af8b-154">`true` - format as number</span></span> |
| <span data-ttu-id="3af8b-155">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="3af8b-155">**Environment variable**</span></span> | <span data-ttu-id="3af8b-156">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-156">N/A</span></span> | <span data-ttu-id="3af8b-157">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="3af8b-157">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="3af8b-158">NLS</span><span class="sxs-lookup"><span data-stu-id="3af8b-158">NLS</span></span>

- <span data-ttu-id="3af8b-159">Określa, czy platforma .NET korzysta z interfejsu API globalizacji języka narodowego (NLS) lub składników międzynarodowych dla aplikacji systemu Windows (ICU).</span><span class="sxs-lookup"><span data-stu-id="3af8b-159">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="3af8b-160">.NET 5,0 i nowsze wersje używają interfejsów API ICU globalizacji domyślnie w systemie Windows 10 maja 2019 Update i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="3af8b-160">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="3af8b-161">W przypadku pominięcia tego ustawienia platforma .NET domyślnie używa interfejsów API ICU globalizacji.</span><span class="sxs-lookup"><span data-stu-id="3af8b-161">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="3af8b-162">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="3af8b-162">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3af8b-163">Aby uzyskać więcej informacji, zobacz [interfejsy API globalizacji korzystają z BIBLIOTEK ICU w systemie Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="3af8b-163">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="3af8b-164">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="3af8b-164">Setting name</span></span> | <span data-ttu-id="3af8b-165">Wartości</span><span class="sxs-lookup"><span data-stu-id="3af8b-165">Values</span></span> | <span data-ttu-id="3af8b-166">Wraca</span><span class="sxs-lookup"><span data-stu-id="3af8b-166">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3af8b-167">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="3af8b-167">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="3af8b-168">`false`-Korzystanie z interfejsów API ICU globalizacji</span><span class="sxs-lookup"><span data-stu-id="3af8b-168">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="3af8b-169">`true`-Korzystanie z interfejsów API globalizacji NLS</span><span class="sxs-lookup"><span data-stu-id="3af8b-169">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="3af8b-170">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3af8b-170">.NET 5.0</span></span> |
| <span data-ttu-id="3af8b-171">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="3af8b-171">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="3af8b-172">`false`-Korzystanie z interfejsów API ICU globalizacji</span><span class="sxs-lookup"><span data-stu-id="3af8b-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="3af8b-173">`true`-Korzystanie z interfejsów API globalizacji NLS</span><span class="sxs-lookup"><span data-stu-id="3af8b-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="3af8b-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="3af8b-174">.NET 5.0</span></span> |
