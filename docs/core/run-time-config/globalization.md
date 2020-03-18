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
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="22d46-103">Opcje konfiguracji w czasie wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="22d46-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="22d46-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="22d46-104">Invariant mode</span></span>

- <span data-ttu-id="22d46-105">Określa, czy aplikacja .NET Core działa w trybie niewariantnym globalizacji bez dostępu do danych i zachowania specyficznych dla kultury, czy też ma dostęp do danych kulturowych.</span><span class="sxs-lookup"><span data-stu-id="22d46-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="22d46-106">Domyślnie: uruchom aplikację z dostępem do danych kulturowych (`false`).</span><span class="sxs-lookup"><span data-stu-id="22d46-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="22d46-107">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="22d46-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="22d46-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="22d46-108">Setting name</span></span> | <span data-ttu-id="22d46-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="22d46-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="22d46-110">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="22d46-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="22d46-111">`false`- dostęp do danych dotyczących kultury</span><span class="sxs-lookup"><span data-stu-id="22d46-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="22d46-112">`true`- uruchomić w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="22d46-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="22d46-113">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="22d46-113">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="22d46-114">`false`- dostęp do danych dotyczących kultury</span><span class="sxs-lookup"><span data-stu-id="22d46-114">`false` - access to cultural data</span></span><br/><span data-ttu-id="22d46-115">`true`- uruchomić w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="22d46-115">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="22d46-116">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="22d46-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="22d46-117">`0`- dostęp do danych dotyczących kultury</span><span class="sxs-lookup"><span data-stu-id="22d46-117">`0` - access to cultural data</span></span><br/><span data-ttu-id="22d46-118">`1`- uruchomić w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="22d46-118">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="22d46-119">Przykłady</span><span class="sxs-lookup"><span data-stu-id="22d46-119">Examples</span></span>

<span data-ttu-id="22d46-120">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="22d46-120">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="22d46-121">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="22d46-121">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="22d46-122">Zakresy roku era</span><span class="sxs-lookup"><span data-stu-id="22d46-122">Era year ranges</span></span>

- <span data-ttu-id="22d46-123">Określa, czy kontrole zakresu dla kalendarzy obsługujących wiele epok są złagodzone, <xref:System.ArgumentOutOfRangeException>czy daty przepełniające zakres dat ery wyrzucające .</span><span class="sxs-lookup"><span data-stu-id="22d46-123">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="22d46-124">Domyślnie: Kontrole zakresu`false`są złagodzone ( ).</span><span class="sxs-lookup"><span data-stu-id="22d46-124">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="22d46-125">Aby uzyskać więcej informacji, zobacz [Kalendarze, eby i zakresy dat: kontrole zakresu złagodzonego](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="22d46-125">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="22d46-126">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="22d46-126">Setting name</span></span> | <span data-ttu-id="22d46-127">Wartości</span><span class="sxs-lookup"><span data-stu-id="22d46-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="22d46-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="22d46-128">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="22d46-129">`false`- rozluźnione kontrole zasięgu</span><span class="sxs-lookup"><span data-stu-id="22d46-129">`false` - relaxed range checks</span></span><br/><span data-ttu-id="22d46-130">`true`- przelewy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="22d46-130">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="22d46-131">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="22d46-131">**Environment variable**</span></span> | <span data-ttu-id="22d46-132">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-132">N/A</span></span> | <span data-ttu-id="22d46-133">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-133">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="22d46-134">Japońskie analizowanie dat</span><span class="sxs-lookup"><span data-stu-id="22d46-134">Japanese date parsing</span></span>

- <span data-ttu-id="22d46-135">Określa, czy ciąg zawierający "1" lub "Gannen" jako rok analizuje pomyślnie lub czy tylko "1" jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="22d46-135">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="22d46-136">Domyślnie: Parse ciągi, które zawierają "1" lub`false`"Gannen" jako rok ( ).</span><span class="sxs-lookup"><span data-stu-id="22d46-136">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="22d46-137">Aby uzyskać więcej informacji, zobacz [Reprezentowanie dat w kalendarzach z wieloma epokami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="22d46-137">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="22d46-138">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="22d46-138">Setting name</span></span> | <span data-ttu-id="22d46-139">Wartości</span><span class="sxs-lookup"><span data-stu-id="22d46-139">Values</span></span> |
| - | - | - |
| <span data-ttu-id="22d46-140">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="22d46-140">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="22d46-141">`false`- "Gannen" lub "1" jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="22d46-141">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="22d46-142">`true`- obsługiwane jest tylko "1"</span><span class="sxs-lookup"><span data-stu-id="22d46-142">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="22d46-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="22d46-143">**Environment variable**</span></span> | <span data-ttu-id="22d46-144">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-144">N/A</span></span> | <span data-ttu-id="22d46-145">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-145">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="22d46-146">Japoński format roku</span><span class="sxs-lookup"><span data-stu-id="22d46-146">Japanese year format</span></span>

- <span data-ttu-id="22d46-147">Określa, czy pierwszy rok ery kalendarza japońskiego jest sformatowany jako "Gannen" czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="22d46-147">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="22d46-148">Domyślnie: Formatuj pierwszy rok`false`jako "Gannen" ( ).</span><span class="sxs-lookup"><span data-stu-id="22d46-148">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="22d46-149">Aby uzyskać więcej informacji, zobacz [Reprezentowanie dat w kalendarzach z wieloma epokami](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="22d46-149">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="22d46-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="22d46-150">Setting name</span></span> | <span data-ttu-id="22d46-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="22d46-151">Values</span></span> |
| - | - | - |
| <span data-ttu-id="22d46-152">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="22d46-152">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="22d46-153">`false`- format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="22d46-153">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="22d46-154">`true`- format jako liczba</span><span class="sxs-lookup"><span data-stu-id="22d46-154">`true` - format as number</span></span> |
| <span data-ttu-id="22d46-155">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="22d46-155">**Environment variable**</span></span> | <span data-ttu-id="22d46-156">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-156">N/A</span></span> | <span data-ttu-id="22d46-157">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="22d46-157">N/A</span></span> |
