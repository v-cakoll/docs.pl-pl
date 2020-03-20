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
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue, funkcja
Konwertuje jedną wartość danych wydajności pierwotnej na określony format lub dwie wartości danych wydajności pierwotnej, jeśli konwersja formatu jest oparta na czasie.

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
[w] Typ licznika. Aby uzyskać listę typów liczników, zobacz [Typy liczników wydajności WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType`może być dowolny typ `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE`licznika z wyjątkiem i .

`dwFormat`\
[w] Format, do którego mają być konwertowane nieprzetworzone dane wydajności. Może to być jedna z następujących wartości:

|Stały  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Zwraca obliczoną wartość jako wartość zmiennoprzecinkową o podwójnej precyzji. |
| `PDH_FMT_LARGE` | 0x00000400 | Zwraca obliczoną wartość jako 64-bitową liczę całkowitą. |
| `PDH_FMT_LONG` | 0x00000100 | Zwraca obliczoną wartość jako 32-bitową liczę całkowitą. |

Jedną z poprzednich wartości może być ORed z jedną z następujących flag skalowania:

|Stały  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nie należy stosować współczynników skalowania licznika. |
| `PDH_FMT_1000` | 0x00002000 | Pomnóż wartość końcową przez 1000. |

`pTimeBase`\
[w] Wskaźnik do podstawy czasu, jeśli to konieczne dla konwersji formatu. Jeśli informacje o podstawie czasu nie są konieczne do konwersji formatu, wartość tego parametru jest ignorowana.

`pRawValue1`\
[w] Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje wartość wydajności nieprzetworzonej.

`pRawValue2`\
[w] Wskaźnik do [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) struktury, która reprezentuje drugą wartość wydajności pierwotnej. Jeśli druga wartość wydajności pierwotnej nie jest `null`konieczna, parametr ten powinien być .

`pFmtValue`\
[na zewnątrz] Wskaźnik do [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) struktury, która otrzymuje sformatowaną wartość wydajności.

## <a name="return-value"></a>Wartość zwracana

Ta funkcja zwraca następujące wartości:

|Stały  |Wartość  |Opis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Wywołanie funkcji zakończy się pomyślnie. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Brak wymaganego argumentu lub niepoprawny. |
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Dojście nie jest prawidłowym obiektem PDH. |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie funkcji [FormatFromRawValue.](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85))

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).

 **Biblioteka:** Perfcounter.dll

 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności WMI i (niezarządzane odwołanie interfejsu API)](index.md)
