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
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue, funkcja
Konwertuje jedną pierwotną wartość danych wydajności do określonego formatu lub dwie wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparta na czasie. 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

`dwCounterType`\
podczas Typ licznika. Aby uzyskać listę typów licznika, zobacz [Typy liczników wydajności usługi WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`może być dowolnego typu licznika z wyjątkiem `PERF_LARGE_RAW_FRACTION` dla `PERF_LARGE_RAW_BASE`i. 

`dwFormat`\
podczas Format, do którego mają zostać przekonwertowane pierwotne dane wydajności. Może to być jedna z następujących wartości:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Zwraca obliczoną wartość jako wartość zmiennoprzecinkową o podwójnej precyzji. | 
| `PDH_FMT_LARGE` | 0x00000400 | Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą. |
| `PDH_FMT_LONG` | 0x00000100 | Zwraca obliczoną wartość jako 32-bitową liczbę całkowitą. |

Jedną z poprzednich wartości można logicznie z jedną z następujących flag skalowania:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nie stosuj czynników skalowania licznika. |
| `PDH_FMT_1000` | 0x00002000 | Pomnóż wartość końcową przez 1 000. | 

`pTimeBase`\
podczas Wskaźnik do podstawy czasu, jeśli jest to konieczne dla konwersji formatu. Jeśli informacje podstawowe czasu nie są niezbędne do konwersji formatu, wartość tego parametru jest ignorowana.

`pRawValue1`\ [in] wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje nieprzetworzoną wartość wydajności.

`pRawValue2`\
podczas Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje drugą pierwotną wartość wydajności. Jeśli druga pierwotna wartość wydajności nie jest konieczna, ten parametr powinien `null`być.

`pFmtValue`\
określoną Wskaźnik do [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) struktury, która otrzymuje sformatowaną wartość wydajności.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca następujące wartości:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Wywołanie funkcji zakończyło się pomyślnie. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Brak wymaganego argumentu lub jest on nieprawidłowy. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Dojście nie jest prawidłowym obiektem PDH. |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie funkcji [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) .

## <a name="requirements"></a>Wymagania

 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Biblioteki** PerfCounter.dll

 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
