---
title: Funkcja FormatFromRawValue (odwołanie do niezarządzanego interfejsu API)
description: Funkcja FormatFromRawValue konwertuje nieprzetworzone dane wydajności na określony format.
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0a7c0b8387f0c8e2b6e2ade94f7efeede75bd758
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176841"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="706de-103">FormatFromRawValue, funkcja</span><span class="sxs-lookup"><span data-stu-id="706de-103">FormatFromRawValue function</span></span>
<span data-ttu-id="706de-104">Konwertuje jedną wartość danych wydajności pierwotnej na określony format lub dwie wartości danych wydajności pierwotnej, jeśli konwersja formatu jest oparta na czasie.</span><span class="sxs-lookup"><span data-stu-id="706de-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="706de-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="706de-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a><span data-ttu-id="706de-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="706de-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="706de-107">[w] Typ licznika.</span><span class="sxs-lookup"><span data-stu-id="706de-107">[in] The counter type.</span></span> <span data-ttu-id="706de-108">Aby uzyskać listę typów liczników, zobacz [Typy liczników wydajności WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="706de-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="706de-109">`dwCounterType`może być dowolny typ `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`licznika z wyjątkiem i .</span><span class="sxs-lookup"><span data-stu-id="706de-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="706de-110">[w] Format, do którego mają być konwertowane nieprzetworzone dane wydajności.</span><span class="sxs-lookup"><span data-stu-id="706de-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="706de-111">Może to być jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="706de-111">It can be one of the following values:</span></span>

|<span data-ttu-id="706de-112">Stały</span><span class="sxs-lookup"><span data-stu-id="706de-112">Constant</span></span>  |<span data-ttu-id="706de-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="706de-113">Value</span></span>  |<span data-ttu-id="706de-114">Opis</span><span class="sxs-lookup"><span data-stu-id="706de-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="706de-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="706de-115">0x00000200</span></span> | <span data-ttu-id="706de-116">Zwraca obliczoną wartość jako wartość zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="706de-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="706de-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="706de-117">0x00000400</span></span> | <span data-ttu-id="706de-118">Zwraca obliczoną wartość jako 64-bitową liczę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="706de-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="706de-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="706de-119">0x00000100</span></span> | <span data-ttu-id="706de-120">Zwraca obliczoną wartość jako 32-bitową liczę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="706de-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="706de-121">Jedną z poprzednich wartości może być ORed z jedną z następujących flag skalowania:</span><span class="sxs-lookup"><span data-stu-id="706de-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="706de-122">Stały</span><span class="sxs-lookup"><span data-stu-id="706de-122">Constant</span></span>  |<span data-ttu-id="706de-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="706de-123">Value</span></span>  |<span data-ttu-id="706de-124">Opis</span><span class="sxs-lookup"><span data-stu-id="706de-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="706de-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="706de-125">0x00001000</span></span> | <span data-ttu-id="706de-126">Nie należy stosować współczynników skalowania licznika.</span><span class="sxs-lookup"><span data-stu-id="706de-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="706de-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="706de-127">0x00002000</span></span> | <span data-ttu-id="706de-128">Pomnóż wartość końcową przez 1000.</span><span class="sxs-lookup"><span data-stu-id="706de-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="706de-129">[w] Wskaźnik do podstawy czasu, jeśli to konieczne dla konwersji formatu.</span><span class="sxs-lookup"><span data-stu-id="706de-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="706de-130">Jeśli informacje o podstawie czasu nie są konieczne do konwersji formatu, wartość tego parametru jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="706de-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="706de-131">[w] Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje wartość wydajności nieprzetworzonej.</span><span class="sxs-lookup"><span data-stu-id="706de-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="706de-132">[w] Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje drugą wartość wydajności pierwotnej.</span><span class="sxs-lookup"><span data-stu-id="706de-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="706de-133">Jeśli druga wartość wydajności pierwotnej nie jest `null`konieczna, parametr ten powinien być .</span><span class="sxs-lookup"><span data-stu-id="706de-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="706de-134">[na zewnątrz] Wskaźnik do [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) struktury, która otrzymuje sformatowaną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="706de-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="706de-135">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="706de-135">Return value</span></span>

<span data-ttu-id="706de-136">Ta funkcja zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="706de-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="706de-137">Stały</span><span class="sxs-lookup"><span data-stu-id="706de-137">Constant</span></span>  |<span data-ttu-id="706de-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="706de-138">Value</span></span>  |<span data-ttu-id="706de-139">Opis</span><span class="sxs-lookup"><span data-stu-id="706de-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="706de-140">0</span><span class="sxs-lookup"><span data-stu-id="706de-140">0</span></span> | <span data-ttu-id="706de-141">Wywołanie funkcji zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="706de-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="706de-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="706de-142">0xC0000BBD</span></span> | <span data-ttu-id="706de-143">Brak wymaganego argumentu lub niepoprawny.</span><span class="sxs-lookup"><span data-stu-id="706de-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="706de-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="706de-144">0xC0000BBC</span></span> | <span data-ttu-id="706de-145">Dojście nie jest prawidłowym obiektem PDH.</span><span class="sxs-lookup"><span data-stu-id="706de-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="706de-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="706de-146">Remarks</span></span>

<span data-ttu-id="706de-147">Ta funkcja zawija wywołanie funkcji [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="706de-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="706de-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="706de-148">Requirements</span></span>

 <span data-ttu-id="706de-149">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="706de-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="706de-150">**Biblioteka:** Perfcounter.dll</span><span class="sxs-lookup"><span data-stu-id="706de-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="706de-151">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="706de-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="706de-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="706de-152">See also</span></span>

- [<span data-ttu-id="706de-153">Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="706de-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
