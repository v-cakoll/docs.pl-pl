---
title: Funkcja GetPropertyHandle (niezarządzany wykaz interfejsów API)
description: Funkcja GetPropertyHandle Zwraca unikatowy uchwytu, który identyfikuje właściwość.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92d48caf7de873850135c7410a5e4b5861131212
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723241"
---
# <a name="getpropertyhandle-function"></a>GetPropertyHandle, funkcja

Zwraca unikatowy uchwytu, który identyfikuje właściwość.

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
[in] Ten parametr jest nieużywany.

`ptr`\
[in] Wskaźnik do [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) wystąpienia.

`wszPropertyName`\
[in] Zakończony znakiem null ciąg kodowany w formacie UTF16 znaków zawierający nazwę właściwości.

`pType`\
[out] Wskaźnik do [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) członka wyliczenia, który reprezentuje typ właściwości w modelu wspólnych informacji.

`pHandle`\
[out] Wskaźnik do liczby całkowitej, który zawiera dojście właściwości.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określona nazwa właściwości nie został znaleziony. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Żądana właściwość jest typu są `CIM_OBJECT` lub `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) metody.

Można użyć tego dojścia do identyfikowania właściwości, korzystając z [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) metod do odczytu lub zapisu wartości właściwości.

Uchwyty można pobrać właściwości wszystkich typów danych innych niż `CIM_OBJECT` i `CIM_ARRAY`. Zwracane uchwyty pracy we wszystkich wystąpieniach klasy.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)