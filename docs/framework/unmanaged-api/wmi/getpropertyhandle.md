---
title: GetPropertyHandle — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetPropertyHandle zwraca unikatowy uchwyt, który identyfikuje właściwość.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 5af003f0295e0b403727f9af6b03ab81c4b8bccb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101859"
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle, funkcja

Zwraca unikatowy uchwyt identyfikujący właściwość.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
podczas Ten parametr jest nieużywany.

`ptr`\
podczas Wskaźnik do wystąpienia [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) .

`wszPropertyName`\
podczas Ciąg zakończony znakiem NULL znaków UTF16, który zawiera nazwę właściwości.

`pType`\
określoną Wskaźnik do elementu członkowskiego wyliczenia [`CIMTYPE`](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) , który reprezentuje typ CIM właściwości.

`pHandle`\
określoną Wskaźnik do liczby całkowitej, która zawiera uchwyt właściwości.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej nazwy właściwości. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Żądana właściwość jest typu `CIM_OBJECT` lub `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) .

Tego uchwytu można użyć do zidentyfikowania właściwości przy użyciu metod [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) do odczytu lub zapisu wartości właściwości.

Dojścia można pobrać dla właściwości wszystkich typów danych innych niż `CIM_OBJECT` i `CIM_ARRAY`. Zwraca obsługę dla wszystkich wystąpień klasy.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils. idl

**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
