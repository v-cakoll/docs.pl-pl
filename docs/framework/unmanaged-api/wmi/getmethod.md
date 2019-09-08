---
title: GetMethod — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetMethod pobiera informacje o metodzie.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798569"
---
# <a name="getmethod-function"></a>GetMethod, funkcja

Pobiera informacje o określonej metodzie.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`\
podczas Nazwa metody. Ten parametr nie może `null` być prawidłowy. `LPCWSTR`

`lFlags`\
podczas Rezerwacj. Ten parametr musi być równy 0.

`ppInSignature`\
określoną Wskaźnik do adresu wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , który opisuje parametry w metodzie. Ten parametr jest ignorowany, jeśli jest ustawiony `null`na.

`ppOutSignature`\
określoną Wskaźnik do adresu wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , który opisuje parametry out metody. Ten parametr jest ignorowany, jeśli jest ustawiony `null`na.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

Zarządzanie systemem Windows może ustawić [](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźnik `null` IWbemClassObject, jeśli metoda nie ma parametrów.

W `ppInSignature` systemach `ppOutSignature` i opisują odpowiednio parametry in i out `IWbemClassObject` , jako właściwości w wystąpieniu klasy systemowej [_Parameters](/windows/desktop/WmiSdk/--parameters). `ppInSignature` Właściwości w `Param`są nazwane *n*, gdzie *n* jest pozycją `Param1` `Param2`parametru w sygnaturze metody (na przykład itp.). Właściwości w `ppOutSignature` są również nazywane `Param` *n*, a zwracaną wartością jest nazwa `ReturnValue`. Aby uzyskać więcej informacji i przykład, zobacz [IWbemClassObject:: GetMethod Metoda](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** WMINet_Utils.idl

**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
