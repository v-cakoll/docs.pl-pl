---
title: FormatFromRawValue — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja FormatFromRawValue konwertuje pierwotne dane wydajności do określonego formatu.
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
ms.openlocfilehash: 5097cfe43ae785461a1e2af1217bcbd5e8c4b79c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120285"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="4c6ac-103">FormatFromRawValue, funkcja</span><span class="sxs-lookup"><span data-stu-id="4c6ac-103">FormatFromRawValue function</span></span>
<span data-ttu-id="4c6ac-104">Konwertuje jedną pierwotną wartość danych wydajności do określonego formatu lub dwie wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparta na czasie.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="4c6ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c6ac-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="4c6ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c6ac-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="4c6ac-107">podczas Typ licznika.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-107">[in] The counter type.</span></span> <span data-ttu-id="4c6ac-108">Aby uzyskać listę typów licznika, zobacz [Typy liczników wydajności usługi WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="4c6ac-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="4c6ac-109">`dwCounterType` może być dowolnego typu licznika z wyjątkiem `PERF_LARGE_RAW_FRACTION` i `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="4c6ac-110">podczas Format, do którego mają zostać przekonwertowane pierwotne dane wydajności.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="4c6ac-111">Może to być jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="4c6ac-111">It can be one of the following values:</span></span>

|<span data-ttu-id="4c6ac-112">Stała</span><span class="sxs-lookup"><span data-stu-id="4c6ac-112">Constant</span></span>  |<span data-ttu-id="4c6ac-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c6ac-113">Value</span></span>  |<span data-ttu-id="4c6ac-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4c6ac-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="4c6ac-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="4c6ac-115">0x00000200</span></span> | <span data-ttu-id="4c6ac-116">Zwraca obliczoną wartość jako wartość zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="4c6ac-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="4c6ac-117">0x00000400</span></span> | <span data-ttu-id="4c6ac-118">Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="4c6ac-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="4c6ac-119">0x00000100</span></span> | <span data-ttu-id="4c6ac-120">Zwraca obliczoną wartość jako 32-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="4c6ac-121">Jedną z poprzednich wartości można logicznie z jedną z następujących flag skalowania:</span><span class="sxs-lookup"><span data-stu-id="4c6ac-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="4c6ac-122">Stała</span><span class="sxs-lookup"><span data-stu-id="4c6ac-122">Constant</span></span>  |<span data-ttu-id="4c6ac-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c6ac-123">Value</span></span>  |<span data-ttu-id="4c6ac-124">Opis</span><span class="sxs-lookup"><span data-stu-id="4c6ac-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="4c6ac-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="4c6ac-125">0x00001000</span></span> | <span data-ttu-id="4c6ac-126">Nie stosuj czynników skalowania licznika.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="4c6ac-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="4c6ac-127">0x00002000</span></span> | <span data-ttu-id="4c6ac-128">Pomnóż wartość końcową przez 1 000.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="4c6ac-129">podczas Wskaźnik do podstawy czasu, jeśli jest to konieczne dla konwersji formatu.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="4c6ac-130">Jeśli informacje podstawowe czasu nie są niezbędne do konwersji formatu, wartość tego parametru jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="4c6ac-131">`pRawValue1`\ [in] wskaźnik do struktury [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , która reprezentuje nieprzetworzoną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="4c6ac-132">podczas Wskaźnik do struktury [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) , która reprezentuje drugą pierwotną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="4c6ac-133">Jeśli druga pierwotna wartość wydajności nie jest konieczna, ten parametr powinien być `null`.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="4c6ac-134">określoną Wskaźnik do struktury [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) , która otrzymuje sformatowaną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c6ac-135">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4c6ac-135">Return value</span></span>

<span data-ttu-id="4c6ac-136">Ta funkcja zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="4c6ac-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="4c6ac-137">Stała</span><span class="sxs-lookup"><span data-stu-id="4c6ac-137">Constant</span></span>  |<span data-ttu-id="4c6ac-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c6ac-138">Value</span></span>  |<span data-ttu-id="4c6ac-139">Opis</span><span class="sxs-lookup"><span data-stu-id="4c6ac-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="4c6ac-140">0</span><span class="sxs-lookup"><span data-stu-id="4c6ac-140">0</span></span> | <span data-ttu-id="4c6ac-141">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="4c6ac-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="4c6ac-142">0xC0000BBD</span></span> | <span data-ttu-id="4c6ac-143">Brak wymaganego argumentu lub jest on nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="4c6ac-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="4c6ac-144">0xC0000BBC</span></span> | <span data-ttu-id="4c6ac-145">Dojście nie jest prawidłowym obiektem PDH.</span><span class="sxs-lookup"><span data-stu-id="4c6ac-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4c6ac-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c6ac-146">Remarks</span></span>

<span data-ttu-id="4c6ac-147">Ta funkcja otacza wywołanie funkcji [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .</span><span class="sxs-lookup"><span data-stu-id="4c6ac-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c6ac-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c6ac-148">Requirements</span></span>

 <span data-ttu-id="4c6ac-149">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c6ac-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="4c6ac-150">**Biblioteka:** Funkcja kończąca PerfCounter. dll</span><span class="sxs-lookup"><span data-stu-id="4c6ac-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="4c6ac-151">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c6ac-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4c6ac-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c6ac-152">See also</span></span>

- [<span data-ttu-id="4c6ac-153">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="4c6ac-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
