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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 681d7ce42b2b8d16353e4f5b3523f1a953a49d95
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037888"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="91620-103">FormatFromRawValue, funkcja</span><span class="sxs-lookup"><span data-stu-id="91620-103">FormatFromRawValue function</span></span>
<span data-ttu-id="91620-104">Konwertuje jedną pierwotną wartość danych wydajności do określonego formatu lub dwie wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparta na czasie.</span><span class="sxs-lookup"><span data-stu-id="91620-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="91620-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="91620-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="91620-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="91620-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="91620-107">podczas Typ licznika.</span><span class="sxs-lookup"><span data-stu-id="91620-107">[in] The counter type.</span></span> <span data-ttu-id="91620-108">Aby uzyskać listę typów licznika, zobacz [Typy liczników wydajności usługi WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="91620-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="91620-109">`dwCounterType`może być dowolnego typu licznika z wyjątkiem `PERF_LARGE_RAW_FRACTION` dla `PERF_LARGE_RAW_BASE`i.</span><span class="sxs-lookup"><span data-stu-id="91620-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="91620-110">podczas Format, do którego mają zostać przekonwertowane pierwotne dane wydajności.</span><span class="sxs-lookup"><span data-stu-id="91620-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="91620-111">Może to być jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="91620-111">It can be one of the following values:</span></span>

|<span data-ttu-id="91620-112">Stała</span><span class="sxs-lookup"><span data-stu-id="91620-112">Constant</span></span>  |<span data-ttu-id="91620-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="91620-113">Value</span></span>  |<span data-ttu-id="91620-114">Opis</span><span class="sxs-lookup"><span data-stu-id="91620-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="91620-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="91620-115">0x00000200</span></span> | <span data-ttu-id="91620-116">Zwraca obliczoną wartość jako wartość zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="91620-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="91620-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="91620-117">0x00000400</span></span> | <span data-ttu-id="91620-118">Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="91620-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="91620-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="91620-119">0x00000100</span></span> | <span data-ttu-id="91620-120">Zwraca obliczoną wartość jako 32-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="91620-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="91620-121">Jedną z poprzednich wartości można logicznie z jedną z następujących flag skalowania:</span><span class="sxs-lookup"><span data-stu-id="91620-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="91620-122">Stała</span><span class="sxs-lookup"><span data-stu-id="91620-122">Constant</span></span>  |<span data-ttu-id="91620-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="91620-123">Value</span></span>  |<span data-ttu-id="91620-124">Opis</span><span class="sxs-lookup"><span data-stu-id="91620-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="91620-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="91620-125">0x00001000</span></span> | <span data-ttu-id="91620-126">Nie stosuj czynników skalowania licznika.</span><span class="sxs-lookup"><span data-stu-id="91620-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="91620-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="91620-127">0x00002000</span></span> | <span data-ttu-id="91620-128">Pomnóż wartość końcową przez 1 000.</span><span class="sxs-lookup"><span data-stu-id="91620-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="91620-129">podczas Wskaźnik do podstawy czasu, jeśli jest to konieczne dla konwersji formatu.</span><span class="sxs-lookup"><span data-stu-id="91620-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="91620-130">Jeśli informacje podstawowe czasu nie są niezbędne do konwersji formatu, wartość tego parametru jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="91620-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="91620-131">`pRawValue1`\ [in] wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje nieprzetworzoną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="91620-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="91620-132">podczas Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje drugą pierwotną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="91620-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="91620-133">Jeśli druga pierwotna wartość wydajności nie jest konieczna, ten parametr powinien `null`być.</span><span class="sxs-lookup"><span data-stu-id="91620-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="91620-134">określoną Wskaźnik do [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) struktury, która otrzymuje sformatowaną wartość wydajności.</span><span class="sxs-lookup"><span data-stu-id="91620-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="91620-135">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="91620-135">Return value</span></span>

<span data-ttu-id="91620-136">Ta funkcja zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="91620-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="91620-137">Stała</span><span class="sxs-lookup"><span data-stu-id="91620-137">Constant</span></span>  |<span data-ttu-id="91620-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="91620-138">Value</span></span>  |<span data-ttu-id="91620-139">Opis</span><span class="sxs-lookup"><span data-stu-id="91620-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="91620-140">0</span><span class="sxs-lookup"><span data-stu-id="91620-140">0</span></span> | <span data-ttu-id="91620-141">Wywołanie funkcji zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="91620-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="91620-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="91620-142">0xC0000BBD</span></span> | <span data-ttu-id="91620-143">Brak wymaganego argumentu lub jest on nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="91620-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="91620-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="91620-144">0xC0000BBC</span></span> | <span data-ttu-id="91620-145">Dojście nie jest prawidłowym obiektem PDH.</span><span class="sxs-lookup"><span data-stu-id="91620-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="91620-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91620-146">Remarks</span></span>

<span data-ttu-id="91620-147">Ta funkcja otacza wywołanie funkcji [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .</span><span class="sxs-lookup"><span data-stu-id="91620-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="91620-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="91620-148">Requirements</span></span>

 <span data-ttu-id="91620-149">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91620-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="91620-150">**Biblioteki** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="91620-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="91620-151">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="91620-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="91620-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91620-152">See also</span></span>

- [<span data-ttu-id="91620-153">WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)</span><span class="sxs-lookup"><span data-stu-id="91620-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
