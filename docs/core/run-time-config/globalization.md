---
title: Ustawienia konfiguracji globalizacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują aspekty globalizacji aplikacji .NET Core, na przykład analizując daty w języku japońskim.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 76cd4a0a0f93f4df3ff243c6024b952576e8e6cb
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740542"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="ffc13-103">Opcje konfiguracji czasu wykonywania dla globalizacji</span><span class="sxs-lookup"><span data-stu-id="ffc13-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="ffc13-104">Tryb niezmienny</span><span class="sxs-lookup"><span data-stu-id="ffc13-104">Invariant mode</span></span>

- <span data-ttu-id="ffc13-105">Określa, czy aplikacja .NET Core działa w trybie niezmiennej globalizacji bez dostępu do danych specyficznych dla kultury i zachowań lub czy ma dostęp do danych kultury.</span><span class="sxs-lookup"><span data-stu-id="ffc13-105">Determines whether a .NET Core app runs in globalization invariant mode without access to culture-specific data and behavior or whether it has access to cultural data.</span></span>
- <span data-ttu-id="ffc13-106">Wartość domyślna: Uruchom aplikację z dostępem do danych kultury (`false`).</span><span class="sxs-lookup"><span data-stu-id="ffc13-106">Default: Run the app with access to cultural data (`false`).</span></span>
- <span data-ttu-id="ffc13-107">Aby uzyskać więcej informacji, zobacz [tryb niezmienny globalizacji platformy .NET Core](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span><span class="sxs-lookup"><span data-stu-id="ffc13-107">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="ffc13-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ffc13-108">Setting name</span></span> | <span data-ttu-id="ffc13-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="ffc13-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ffc13-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="ffc13-110">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="ffc13-111">`false` dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="ffc13-111">`false` - access to cultural data</span></span><br/><span data-ttu-id="ffc13-112">`true` — uruchamianie w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="ffc13-112">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="ffc13-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ffc13-113">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="ffc13-114">`0` dostęp do danych kultury</span><span class="sxs-lookup"><span data-stu-id="ffc13-114">`0` - access to cultural data</span></span><br/><span data-ttu-id="ffc13-115">`1` — uruchamianie w trybie niezmiennym</span><span class="sxs-lookup"><span data-stu-id="ffc13-115">`1` - run in invariant mode</span></span> |

## <a name="era-year-ranges"></a><span data-ttu-id="ffc13-116">Zakresy lat era</span><span class="sxs-lookup"><span data-stu-id="ffc13-116">Era year ranges</span></span>

- <span data-ttu-id="ffc13-117">Określa, czy zakres sprawdza, czy kalendarze obsługujące wiele operacji wymazywania są swobodne, czy też czy daty, które przepełnią zakres dat ERA, zgłaszają <xref:System.ArgumentOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="ffc13-117">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="ffc13-118">Domyślne: Sprawdzanie zakresu jest swobodne (`false`).</span><span class="sxs-lookup"><span data-stu-id="ffc13-118">Default: Range checks are relaxed (`false`).</span></span>
- <span data-ttu-id="ffc13-119">Aby uzyskać więcej informacji, zobacz [kalendarze, wymazywane i zakres dat: kontrole swobodnego zakresu](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span><span class="sxs-lookup"><span data-stu-id="ffc13-119">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="ffc13-120">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ffc13-120">Setting name</span></span> | <span data-ttu-id="ffc13-121">Wartości</span><span class="sxs-lookup"><span data-stu-id="ffc13-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ffc13-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="ffc13-122">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="ffc13-123">kontrole zakresu swobodnego `false`</span><span class="sxs-lookup"><span data-stu-id="ffc13-123">`false` - relaxed range checks</span></span><br/><span data-ttu-id="ffc13-124">`true` — nadprzepływy powodują wyjątek</span><span class="sxs-lookup"><span data-stu-id="ffc13-124">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="ffc13-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ffc13-125">**Environment variable**</span></span> | <span data-ttu-id="ffc13-126">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-126">N/A</span></span> | <span data-ttu-id="ffc13-127">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-127">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="ffc13-128">Japońska analiza daty</span><span class="sxs-lookup"><span data-stu-id="ffc13-128">Japanese date parsing</span></span>

- <span data-ttu-id="ffc13-129">Określa, czy ciąg, który zawiera "1" lub "Gannen", jest analizowany pomyślnie, czy jest obsługiwany tylko "1".</span><span class="sxs-lookup"><span data-stu-id="ffc13-129">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="ffc13-130">Domyślnie: Przeanalizuj ciągi, które zawierają "1" lub "Gannen" jako rok (`false`).</span><span class="sxs-lookup"><span data-stu-id="ffc13-130">Default: Parse strings that contain either "1" or "Gannen" as the year (`false`).</span></span>
- <span data-ttu-id="ffc13-131">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="ffc13-131">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="ffc13-132">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ffc13-132">Setting name</span></span> | <span data-ttu-id="ffc13-133">Wartości</span><span class="sxs-lookup"><span data-stu-id="ffc13-133">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ffc13-134">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="ffc13-134">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="ffc13-135">`false` — obsługiwana jest wartość "Gannen" lub "1"</span><span class="sxs-lookup"><span data-stu-id="ffc13-135">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="ffc13-136">Obsługiwane są tylko `true` "1"</span><span class="sxs-lookup"><span data-stu-id="ffc13-136">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="ffc13-137">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ffc13-137">**Environment variable**</span></span> | <span data-ttu-id="ffc13-138">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-138">N/A</span></span> | <span data-ttu-id="ffc13-139">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-139">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="ffc13-140">Japoński rok</span><span class="sxs-lookup"><span data-stu-id="ffc13-140">Japanese year format</span></span>

- <span data-ttu-id="ffc13-141">Określa, czy pierwszy rok dla ery w kalendarzu japońskim jest sformatowany jako "Gannen", czy jako liczba.</span><span class="sxs-lookup"><span data-stu-id="ffc13-141">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="ffc13-142">Domyślnie: Formatuj pierwszy rok jako "Gannen" (`false`).</span><span class="sxs-lookup"><span data-stu-id="ffc13-142">Default: Format the first year as "Gannen" (`false`).</span></span>
- <span data-ttu-id="ffc13-143">Aby uzyskać więcej informacji, zobacz [przedstawianie dat w kalendarzach z wieloma wymazywanymi](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span><span class="sxs-lookup"><span data-stu-id="ffc13-143">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="ffc13-144">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ffc13-144">Setting name</span></span> | <span data-ttu-id="ffc13-145">Wartości</span><span class="sxs-lookup"><span data-stu-id="ffc13-145">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ffc13-146">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="ffc13-146">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="ffc13-147">`false`-format jako "Gannen"</span><span class="sxs-lookup"><span data-stu-id="ffc13-147">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="ffc13-148">`true` — formatowanie jako liczba</span><span class="sxs-lookup"><span data-stu-id="ffc13-148">`true` - format as number</span></span> |
| <span data-ttu-id="ffc13-149">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ffc13-149">**Environment variable**</span></span> | <span data-ttu-id="ffc13-150">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-150">N/A</span></span> | <span data-ttu-id="ffc13-151">N/D</span><span class="sxs-lookup"><span data-stu-id="ffc13-151">N/A</span></span> |
