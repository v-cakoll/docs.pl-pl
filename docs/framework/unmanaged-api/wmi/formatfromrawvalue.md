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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609051"
---
# <a name="formatfromrawvalue-function"></a>FormatFromRawValue, funkcja
Konwertuje jedną wartość danych pierwotnych wydajności w określonym formacie lub dwóch wartości danych pierwotnych wydajności, jeśli Konwersja formatu jest oparte na czasie. 

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

`dwCounterType`\
[in] Typ licznika. Aby uzyskać listę typów liczników, zobacz [typy licznika wydajności WMI](/windows/desktop/WmiSdk/wmi-performance-counter-types). `dwCounterType` mogą być dowolnego typu liczników, z wyjątkiem `PERF_LARGE_RAW_FRACTION` i `PERF_LARGE_RAW_BASE`. 

`dwFormat`\
[in] Format, do którego można przekonwertować pierwotnych danych wydajności. Może to być jedna z następujących wartości:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |0x00000200 | Zwraca obliczoną wartość jako wartość punktu zmiennoprzecinkową podwójnej precyzji. | 
| `PDH_FMT_LARGE` | 0x00000400 | Zwraca obliczoną wartość jako 64-bitową liczbę całkowitą. |
| `PDH_FMT_LONG` | 0x00000100 | Zwraca obliczoną wartość jako 32-bitową liczbę całkowitą. |

Jedną z poprzednimi wartościami może być operacja logiczna przy użyciu jednego z następujących flag skalowania:

|Stała  |Wartość  |Opis |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | 0x00001000 | Nie należy stosować ten licznik skalowania czynników. |
| `PDH_FMT_1000` | 0x00002000 | Za 1000, należy pomnożyć wartość końcową. | 

`pTimeBase`\
[in] Wskaźnik do podstawowego czasu, jeśli jest to niezbędne do konwersji formatów. Jeśli podstawowy informacje o czasie nie jest niezbędne do konwersji formatów, wartość tego parametru jest ignorowana.

`pRawValue1`\ [in] wskaźnik do [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) strukturę, która reprezentuje wartość wydajność pierwotna.

`pRawValue2`\
[in] Wskaźnik do [ `PDH_RAW_COUNTER` ](/windows/desktop/api/pdh/ns-pdh-_pdh_raw_counter) strukturę, która reprezentuje wartość drugiego wydajność pierwotna. Jeśli drugiej wartości pierwotnych wydajności nie jest konieczne, ten parametr powinien być `null`.

`pFmtValue`\
[out] Wskaźnik do [ `PDH_FMT_COUNTERVALUE` ](/windows/desktop/api/pdh/ns-pdh-_pdh_fmt_countervalue) struktury, który odbiera wartość wydajności sformatowany.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości są zwracane przez tę funkcję:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `ERROR_SUCCESS` | 0 | Wywołanie funkcji zakończy się pomyślnie. |
| `PDH_INVALID_ARGUMENT` | 0xC0000BBD | Wymagany argument jest brakujące lub nieprawidłowe. | 
| `PDH_INVALID_HANDLE` | 0xC0000BBC | Dojście nie jest prawidłowym obiektem PDH. |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [FormatFromRawValue](https://docs.microsoft.com/previous-versions/ms231047(v=vs.85)) funkcji.

## <a name="requirements"></a>Wymagania

 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

 **Biblioteka:** PerfCounter.dll

 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
