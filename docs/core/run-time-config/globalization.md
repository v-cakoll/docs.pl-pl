---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: 56228e9a6cb6dbab6a22bdc00d11212e1019776b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761970"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="0ab14-103">Opcje konfiguracji czasu wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="0ab14-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="0ab14-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="0ab14-104">Invariant mode</span></span>

- <span data-ttu-id="0ab14-105">Określa, czy aplikacja .NET Core działa w trybie globalizacji-niezmiennym bez dostępu do danych i zachowań specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="0ab14-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="0ab14-106">Jeśli pominięto to ustawienie, aplikacja zostanie uruchomiona z dostępem do danych kultury.</span><span class="sxs-lookup"><span data-stu-id="0ab14-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="0ab14-107">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="0ab14-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0ab14-108">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="0ab14-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="0ab14-109">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0ab14-109">Setting name</span></span> | <span data-ttu-id="0ab14-110">Wartości</span><span class="sxs-lookup"><span data-stu-id="0ab14-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0ab14-111">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0ab14-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="0ab14-112">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="0ab14-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="0ab14-113">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="0ab14-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0ab14-114">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="0ab14-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="0ab14-115">`false`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="0ab14-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="0ab14-116">`true`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="0ab14-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="0ab14-117">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0ab14-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="0ab14-118">`0`— dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="0ab14-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="0ab14-119">`1`-Uruchom w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="0ab14-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="0ab14-120">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0ab14-120">Examples</span></span>

<span data-ttu-id="0ab14-121">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="0ab14-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="0ab14-122">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="0ab14-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="0ab14-123">Zakresy lat era</span><span class="sxs-lookup"><span data-stu-id="0ab14-123">Era year ranges</span></span>

- <span data-ttu-id="0ab14-124">Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też wskazuje, czy daty, które przepełnią zakres dat era <xref:System.ArgumentOutOfRangeException> .</span><span class="sxs-lookup"><span data-stu-id="0ab14-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="0ab14-125">W przypadku pominięcia tego ustawienia testy zakresu są swobodne.</span><span class="sxs-lookup"><span data-stu-id="0ab14-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="0ab14-126">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="0ab14-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0ab14-127">Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="0ab14-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="0ab14-128">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0ab14-128">Setting name</span></span> | <span data-ttu-id="0ab14-129">Wartości</span><span class="sxs-lookup"><span data-stu-id="0ab14-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0ab14-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0ab14-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="0ab14-131">`false`-swobodne kontrole zakresu</span><span class="sxs-lookup"><span data-stu-id="0ab14-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="0ab14-132">`true`-nadprzepływy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="0ab14-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="0ab14-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0ab14-133">**Environment variable**</span></span> | <span data-ttu-id="0ab14-134">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-134">N/A</span></span> | <span data-ttu-id="0ab14-135">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="0ab14-136">Japońska analiza daty</span><span class="sxs-lookup"><span data-stu-id="0ab14-136">Japanese date parsing</span></span>

- <span data-ttu-id="0ab14-137">Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".</span><span class="sxs-lookup"><span data-stu-id="0ab14-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="0ab14-138">Jeśli pominięto to ustawienie, ciągi zawierające wartość "1" lub "Gannen" w przypadku pomyślnego przeanalizowania roku.</span><span class="sxs-lookup"><span data-stu-id="0ab14-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="0ab14-139">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="0ab14-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0ab14-140">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0ab14-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0ab14-141">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0ab14-141">Setting name</span></span> | <span data-ttu-id="0ab14-142">Wartości</span><span class="sxs-lookup"><span data-stu-id="0ab14-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0ab14-143">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0ab14-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="0ab14-144">`false`-Jest obsługiwana wartość "Gannen" lub "1"</span><span class="sxs-lookup"><span data-stu-id="0ab14-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="0ab14-145">`true`-tylko "1" jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="0ab14-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="0ab14-146">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0ab14-146">**Environment variable**</span></span> | <span data-ttu-id="0ab14-147">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-147">N/A</span></span> | <span data-ttu-id="0ab14-148">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="0ab14-149">Japoński rok</span><span class="sxs-lookup"><span data-stu-id="0ab14-149">Japanese year format</span></span>

- <span data-ttu-id="0ab14-150">Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="0ab14-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="0ab14-151">Jeśli to ustawienie zostanie pominięte, pierwszy rok zostanie sformatowany jako "Gannen".</span><span class="sxs-lookup"><span data-stu-id="0ab14-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="0ab14-152">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="0ab14-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0ab14-153">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="0ab14-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="0ab14-154">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0ab14-154">Setting name</span></span> | <span data-ttu-id="0ab14-155">Wartości</span><span class="sxs-lookup"><span data-stu-id="0ab14-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0ab14-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0ab14-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="0ab14-157">`false`-Format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="0ab14-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="0ab14-158">`true`-formatowanie jako liczba</span><span class="sxs-lookup"><span data-stu-id="0ab14-158">`true` - format as number</span></span> |
| <span data-ttu-id="0ab14-159">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0ab14-159">**Environment variable**</span></span> | <span data-ttu-id="0ab14-160">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-160">N/A</span></span> | <span data-ttu-id="0ab14-161">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="0ab14-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="0ab14-162">NLS</span><span class="sxs-lookup"><span data-stu-id="0ab14-162">NLS</span></span>

- <span data-ttu-id="0ab14-163">Określa, czy platforma .NET korzysta z interfejsu API globalizacji języka narodowego (NLS) lub składników międzynarodowych dla aplikacji systemu Windows (ICU).</span><span class="sxs-lookup"><span data-stu-id="0ab14-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="0ab14-164">.NET 5,0 i nowsze wersje używają interfejsów API ICU globalizacji domyślnie w systemie Windows 10 maja 2019 Update i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="0ab14-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="0ab14-165">W przypadku pominięcia tego ustawienia platforma .NET domyślnie używa interfejsów API ICU globalizacji.</span><span class="sxs-lookup"><span data-stu-id="0ab14-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="0ab14-166">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="0ab14-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="0ab14-167">Aby uzyskać więcej informacji, zobacz [interfejsy API globalizacji korzystają z BIBLIOTEK ICU w systemie Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span><span class="sxs-lookup"><span data-stu-id="0ab14-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/3.1-5.0.md#globalization-apis-use-icu-libraries-on-windows).</span></span>

| | <span data-ttu-id="0ab14-168">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0ab14-168">Setting name</span></span> | <span data-ttu-id="0ab14-169">Wartości</span><span class="sxs-lookup"><span data-stu-id="0ab14-169">Values</span></span> | <span data-ttu-id="0ab14-170">Wraca</span><span class="sxs-lookup"><span data-stu-id="0ab14-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="0ab14-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="0ab14-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="0ab14-172">`false`-Korzystanie z interfejsów API ICU globalizacji</span><span class="sxs-lookup"><span data-stu-id="0ab14-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="0ab14-173">`true`-Korzystanie z interfejsów API globalizacji NLS</span><span class="sxs-lookup"><span data-stu-id="0ab14-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="0ab14-174">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0ab14-174">.NET 5.0</span></span> |
| <span data-ttu-id="0ab14-175">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0ab14-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="0ab14-176">`false`-Korzystanie z interfejsów API ICU globalizacji</span><span class="sxs-lookup"><span data-stu-id="0ab14-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="0ab14-177">`true`-Korzystanie z interfejsów API globalizacji NLS</span><span class="sxs-lookup"><span data-stu-id="0ab14-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="0ab14-178">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="0ab14-178">.NET 5.0</span></span> |
