---
title: "Funkcja FormatFromRawValue (niezarządzany wykaz interfejsów API)"
description: "Funkcja FormatFromRawValue konwertuje pierwotnych danych wydajności w określonym formacie."
ms.date: 11/21/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3daa89ec0b40bb9c08898ecd682f05f0f0ce09a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="formatfromrawvalue-function"></a>Funkcja FormatFromRawValue
Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych wydajność pierwotna, jeśli Konwersja formatu jest oparte na czasie.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
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

## <a name="parameters"></a>Parametry

`dwCounterType`  
[in] Typ licznika. Listę typów licznika, zobacz [typy licznika wydajności WMI](https://msdn.microsoft.com/library/aa394569(v=vs.85).aspx). `dwCounterType`mogą być dowolnego typu licznika, z wyjątkiem `PERF_LARGE_RAW_FRACTION` i `PERF_LARGE_RAW_BASE`. 

`dwFormat`  
[in] Format, do którego można przekonwertować pierwotnych danych wydajności. Może być jedną z następujących wartości:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Zwraca obliczoną wartość jako wartość podwójnej precyzji ruchomy punkt. | 
| `PDH_FMT_LARGE` | 0x00000400 | Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą. |
| `PDH_FMT_LONG` | 0x00000100 | Zwraca obliczoną wartość jako liczba całkowita 32-bitowych. |

Jedną z poprzednimi wartościami może być operacja logiczna z jednym z następujących flag skalowania:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nie stosuj czynniki skalowania licznika. |
| `PDH_FMT_1000` | 0x00002000 | Należy pomnożyć końcowej przez 1000. | 

`pTimeBase`  
[in] Wskaźnik do podstawy czasu, jeśli to konieczne do konwersji na format. Jeśli podstawowe informacje o czasie nie jest niezbędna dla Konwersja formatu, wartość tego parametru jest ignorowana.

`pRawValue1`[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) strukturę, która reprezentuje wydajność pierwotna wartość.

`pRawValue2`[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](https://msdn.microsoft.com/library/windows/desktop/aa373060(v=vs.85).aspx) strukturę, która reprezentuje druga wartość wydajność pierwotna. Jeśli drugiej wartości wydajność pierwotna nie jest konieczne, ten parametr powinien być `null`.

`pFmtValue`[out] Wskaźnik do [ `PDH_FMT_COUNTERVALUE` ](https://msdn.microsoft.com/library/windows/desktop/aa373050(v=vs.85).aspx) struktury, który odbiera wartość wydajności sformatowany.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości są zwracane przez tę funkcję:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Wywołanie funkcji zakończy się pomyślnie. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Wymagany argument jest niewystarczające lub niepoprawne. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Dojście nie jest prawidłowym obiektem PDH. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [FormatFromRawValue](https://msdn.microsoft.com/library/ms231047(v=vs.85).aspx) funkcji.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Biblioteka:** PerfCounter.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
