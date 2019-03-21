---
title: Funkcja FormatFromRawValue (niezarządzany wykaz interfejsów API)
description: Funkcja FormatFromRawValue konwertuje pierwotnych danych wydajności w określonym formacie.
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
ms.openlocfilehash: 44a84b03c85cc1332c07ffbaf53187b7f01d0236
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262469"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="33919-103">Funkcja FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="33919-103">FormatFromRawValue function</span></span>
<span data-ttu-id="33919-104">Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparte na czasie.</span><span class="sxs-lookup"><span data-stu-id="33919-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="33919-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="33919-105">Syntax</span></span>

```
int FormatFromRawValue (
   [in] uint                    dwCounterType, 
   [in] uint                    dwFormat, 
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
); 
```

## <a name="parameters"></a><span data-ttu-id="33919-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33919-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="33919-107">[in] Typ licznika.</span><span class="sxs-lookup"><span data-stu-id="33919-107">[in] The counter type.</span></span> <span data-ttu-id="33919-108">Aby uzyskać listę typów liczników, zobacz [typy licznika wydajności WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span><span class="sxs-lookup"><span data-stu-id="33919-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="33919-109">`dwCounterType` mogą być dowolnego typu liczników, z wyjątkiem `PERF_LARGE_RAW_FRACTION` i `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="33919-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`\
<span data-ttu-id="33919-110">[in] Format, do którego można przekonwertować pierwotnych danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="33919-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="33919-111">Może to być jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="33919-111">It can be one of the following values:</span></span>

|<span data-ttu-id="33919-112">Stała</span><span class="sxs-lookup"><span data-stu-id="33919-112">Constant</span></span>  |<span data-ttu-id="33919-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="33919-113">Value</span></span>  |<span data-ttu-id="33919-114">Opis</span><span class="sxs-lookup"><span data-stu-id="33919-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="33919-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="33919-115">0x00000200</span></span> | <span data-ttu-id="33919-116">Zwraca obliczoną wartość jako wartość punktu zmiennoprzecinkową podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="33919-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="33919-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="33919-117">0x00000400</span></span> | <span data-ttu-id="33919-118">Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="33919-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="33919-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="33919-119">0x00000100</span></span> | <span data-ttu-id="33919-120">Zwraca obliczoną wartość jako 32-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="33919-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="33919-121">Jedną z poprzednimi wartościami może być operacja logiczna przy użyciu jednego z następujących flag skalowania:</span><span class="sxs-lookup"><span data-stu-id="33919-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="33919-122">Stała</span><span class="sxs-lookup"><span data-stu-id="33919-122">Constant</span></span>  |<span data-ttu-id="33919-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="33919-123">Value</span></span>  |<span data-ttu-id="33919-124">Opis</span><span class="sxs-lookup"><span data-stu-id="33919-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="33919-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="33919-125">0x00001000</span></span> | <span data-ttu-id="33919-126">Nie należy stosować ten licznik skalowania czynników.</span><span class="sxs-lookup"><span data-stu-id="33919-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="33919-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="33919-127">0x00002000</span></span> | <span data-ttu-id="33919-128">Za 1000, należy pomnożyć wartość końcową.</span><span class="sxs-lookup"><span data-stu-id="33919-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`\
<span data-ttu-id="33919-129">[in] Wskaźnik do podstawowego czasu, jeśli jest to niezbędne do konwersji formatów.</span><span class="sxs-lookup"><span data-stu-id="33919-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="33919-130">Jeśli podstawowy informacje o czasie nie jest niezbędne do konwersji formatów, wartość tego parametru jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="33919-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="33919-131">`pRawValue1`\ [in] wskaźnik do [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) strukturę, która reprezentuje wartość wydajność pierwotna.</span><span class="sxs-lookup"><span data-stu-id="33919-131">`pRawValue1`\ [in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="33919-132">[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) strukturę, która reprezentuje wartość drugiego wydajność pierwotna.</span><span class="sxs-lookup"><span data-stu-id="33919-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="33919-133">Jeśli drugiej wartości pierwotnych wydajności nie jest konieczne, ten parametr powinien być `null`.</span><span class="sxs-lookup"><span data-stu-id="33919-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="33919-134">[out] Wskaźnik do [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) struktury, który odbiera wartość wydajności sformatowany.</span><span class="sxs-lookup"><span data-stu-id="33919-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="33919-135">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33919-135">Return value</span></span>

<span data-ttu-id="33919-136">Następujące wartości są zwracane przez tę funkcję:</span><span class="sxs-lookup"><span data-stu-id="33919-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="33919-137">Stała</span><span class="sxs-lookup"><span data-stu-id="33919-137">Constant</span></span>  |<span data-ttu-id="33919-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="33919-138">Value</span></span>  |<span data-ttu-id="33919-139">Opis</span><span class="sxs-lookup"><span data-stu-id="33919-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="33919-140">0</span><span class="sxs-lookup"><span data-stu-id="33919-140">0</span></span> | <span data-ttu-id="33919-141">Wywołanie funkcji zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="33919-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="33919-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="33919-142">0xC0000BBD</span></span> | <span data-ttu-id="33919-143">Wymagany argument jest brakujące lub nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="33919-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="33919-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="33919-144">0xC0000BBC</span></span> | <span data-ttu-id="33919-145">Dojście nie jest prawidłowym obiektem PDH.</span><span class="sxs-lookup"><span data-stu-id="33919-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="33919-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33919-146">Remarks</span></span>

<span data-ttu-id="33919-147">Ta funkcja zawija wywołanie do [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) funkcji.</span><span class="sxs-lookup"><span data-stu-id="33919-147">This function wraps a call to the [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="33919-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33919-148">Requirements</span></span>

 <span data-ttu-id="33919-149">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33919-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="33919-150">**Biblioteka:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="33919-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="33919-151">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="33919-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="33919-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33919-152">See also</span></span>

- [<span data-ttu-id="33919-153">Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)</span><span class="sxs-lookup"><span data-stu-id="33919-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
