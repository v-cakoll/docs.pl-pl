---
title: "Funkcja FormatFromRawValue (niezarządzany wykaz interfejsów API)"
description: "Funkcja FormatFromRawValue konwertuje pierwotnych danych wydajności w określonym formacie."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: FormatFromRawValue
api_location: PerfCounter.dll
api_type: DLLExport
f1_keywords: FormatFromRawValue
helpviewer_keywords: FormatFromRawValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c01db47b5362d7048e2e5ecd1b63acfe03eff860
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="9ed36-103">Funkcja FormatFromRawValue</span><span class="sxs-lookup"><span data-stu-id="9ed36-103">FormatFromRawValue function</span></span>
<span data-ttu-id="9ed36-104">Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych wydajność pierwotna, jeśli Konwersja formatu jest oparte na czasie.</span><span class="sxs-lookup"><span data-stu-id="9ed36-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9ed36-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ed36-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="9ed36-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9ed36-106">Parameters</span></span>

`dwCounterType`  
<span data-ttu-id="9ed36-107">[in] Typ licznika.</span><span class="sxs-lookup"><span data-stu-id="9ed36-107">[in] The counter type.</span></span> <span data-ttu-id="9ed36-108">Listę typów licznika, zobacz [typy licznika wydajności WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="9ed36-108">For a list of counter types, see [WMI Performance Counter Types](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx).</span></span> <span data-ttu-id="9ed36-109">`dwCounterType`mogą być dowolnego typu licznika, z wyjątkiem `PERF_LARGE_RAW_FRACTION` i `PERF_LARGE_RAW_BASE`.</span><span class="sxs-lookup"><span data-stu-id="9ed36-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span> 

`dwFormat`  
<span data-ttu-id="9ed36-110">[in] Format, do którego można przekonwertować pierwotnych danych wydajności.</span><span class="sxs-lookup"><span data-stu-id="9ed36-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="9ed36-111">Może być jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="9ed36-111">It can be one of the following values:</span></span>

|<span data-ttu-id="9ed36-112">Stała</span><span class="sxs-lookup"><span data-stu-id="9ed36-112">Constant</span></span>  |<span data-ttu-id="9ed36-113">Wartość</span><span class="sxs-lookup"><span data-stu-id="9ed36-113">Value</span></span>  |<span data-ttu-id="9ed36-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed36-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="9ed36-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="9ed36-115">0x00000200</span></span> | <span data-ttu-id="9ed36-116">Zwraca obliczoną wartość jako wartość podwójnej precyzji ruchomy punkt.</span><span class="sxs-lookup"><span data-stu-id="9ed36-116">Return the calculated value as a double-precision floating point value.</span></span> | 
| `PDH_FMT_LARGE` | <span data-ttu-id="9ed36-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="9ed36-117">0x00000400</span></span> | <span data-ttu-id="9ed36-118">Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="9ed36-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="9ed36-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="9ed36-119">0x00000100</span></span> | <span data-ttu-id="9ed36-120">Zwraca obliczoną wartość jako liczba całkowita 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="9ed36-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="9ed36-121">Jedną z poprzednimi wartościami może być operacja logiczna z jednym z następujących flag skalowania:</span><span class="sxs-lookup"><span data-stu-id="9ed36-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="9ed36-122">Stała</span><span class="sxs-lookup"><span data-stu-id="9ed36-122">Constant</span></span>  |<span data-ttu-id="9ed36-123">Wartość</span><span class="sxs-lookup"><span data-stu-id="9ed36-123">Value</span></span>  |<span data-ttu-id="9ed36-124">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed36-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="9ed36-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="9ed36-125">0x00001000</span></span> | <span data-ttu-id="9ed36-126">Nie stosuj czynniki skalowania licznika.</span><span class="sxs-lookup"><span data-stu-id="9ed36-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="9ed36-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="9ed36-127">0x00002000</span></span> | <span data-ttu-id="9ed36-128">Należy pomnożyć końcowej przez 1000.</span><span class="sxs-lookup"><span data-stu-id="9ed36-128">Multiply the final value by 1,000.</span></span> | 

`pTimeBase`  
<span data-ttu-id="9ed36-129">[in] Wskaźnik do podstawy czasu, jeśli to konieczne do konwersji na format.</span><span class="sxs-lookup"><span data-stu-id="9ed36-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="9ed36-130">Jeśli podstawowe informacje o czasie nie jest niezbędna dla Konwersja formatu, wartość tego parametru jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="9ed36-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

<span data-ttu-id="9ed36-131">`pRawValue1`[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) strukturę, która reprezentuje wydajność pierwotna wartość.</span><span class="sxs-lookup"><span data-stu-id="9ed36-131">`pRawValue1` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a raw performance value.</span></span>

<span data-ttu-id="9ed36-132">`pRawValue2`[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) strukturę, która reprezentuje druga wartość wydajność pierwotna.</span><span class="sxs-lookup"><span data-stu-id="9ed36-132">`pRawValue2` [in] A pointer to a [`PDH_RAW_COUNTER`](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) structure that represents a second raw performance value.</span></span> <span data-ttu-id="9ed36-133">Jeśli drugiej wartości wydajność pierwotna nie jest konieczne, ten parametr powinien być `null`.</span><span class="sxs-lookup"><span data-stu-id="9ed36-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

<span data-ttu-id="9ed36-134">`pFmtValue`[out] Wskaźnik do [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) struktury, który odbiera wartość wydajności sformatowany.</span><span class="sxs-lookup"><span data-stu-id="9ed36-134">`pFmtValue` [out] A pointer to a [`PDH_FMT_COUNTERVALUE`](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ed36-135">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9ed36-135">Return value</span></span>

<span data-ttu-id="9ed36-136">Następujące wartości są zwracane przez tę funkcję:</span><span class="sxs-lookup"><span data-stu-id="9ed36-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="9ed36-137">Stała</span><span class="sxs-lookup"><span data-stu-id="9ed36-137">Constant</span></span>  |<span data-ttu-id="9ed36-138">Wartość</span><span class="sxs-lookup"><span data-stu-id="9ed36-138">Value</span></span>  |<span data-ttu-id="9ed36-139">Opis</span><span class="sxs-lookup"><span data-stu-id="9ed36-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="9ed36-140">0</span><span class="sxs-lookup"><span data-stu-id="9ed36-140">0</span></span> | <span data-ttu-id="9ed36-141">Wywołanie funkcji zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9ed36-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="9ed36-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="9ed36-142">0xC0000BBD</span></span> | <span data-ttu-id="9ed36-143">Wymagany argument jest niewystarczające lub niepoprawne.</span><span class="sxs-lookup"><span data-stu-id="9ed36-143">A required argument is missing or incorrect.</span></span> | 
| `PDH_INVALID_HANDLE` | <span data-ttu-id="9ed36-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="9ed36-144">0xC0000BBC</span></span> | <span data-ttu-id="9ed36-145">Dojście nie jest prawidłowym obiektem PDH.</span><span class="sxs-lookup"><span data-stu-id="9ed36-145">The handle is not a valid PDH object.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="9ed36-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ed36-146">Remarks</span></span>

<span data-ttu-id="9ed36-147">Ta funkcja jest zawijana wywołanie [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) funkcji.</span><span class="sxs-lookup"><span data-stu-id="9ed36-147">This function wraps a call to the [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="9ed36-148">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ed36-148">Requirements</span></span>  
 <span data-ttu-id="9ed36-149">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed36-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed36-150">**Biblioteka:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="9ed36-150">**Library:** PerfCounter.dll</span></span>  
  
 <span data-ttu-id="9ed36-151">**Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed36-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed36-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ed36-152">See also</span></span>  
[<span data-ttu-id="9ed36-153">Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI</span><span class="sxs-lookup"><span data-stu-id="9ed36-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
