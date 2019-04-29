---
title: Funkcja GetMethod (niezarządzany wykaz interfejsów API)
description: Funkcja getmethod — pobiera informacje dotyczące metody.
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
ms.openlocfilehash: cb8919e8760616676ea5ff99069e2d2ceb5f7451
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608921"
---
# <a name="getmethod-function"></a>GetMethod, funkcja

Pobiera informacje o określonej metody.

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
[in] Ten parametr jest nieużywany.

`ptr`\
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszName`\
[in] Nazwa metody. Ten parametr nie może być `null` i musi się odnosić do prawidłowego `LPCWSTR`.

`lFlags`\
[in] Zastrzeżone. Ten parametr musi być 0.

`ppInSignature`\
[out] Wskaźnik na adres [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienie, które opisano w parametrów do metody. Ten parametr jest ignorowany, jeśli jest równa `null`.

`ppOutSignature`\
[out] Wskaźnik na adres [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienie, które opisuje poza parametrów do metody. Ten parametr jest ignorowany, jeśli jest równa `null`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.

Windows Management można ustawić [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wskaźnik do `null` Jeśli metoda nie ma w parametrów.

W `ppInSignature` i `ppOutSignature` opisano parametry, wejściowe i wyjściowe odpowiednio właściwości w `IWbemClassObject` wystąpienia klasy systemu [_Parameters](/windows/desktop/WmiSdk/--parameters). Właściwości w `ppInSignature` noszą `Param` *n*, gdzie *n* to pozycja parametru w podpisie metody (takie jak `Param1`, `Param2`itp.). Właściwości w `ppOutSignature` są również nazywane `Param` *n*, i wartość zwracaną nosi nazwę `ReturnValue`. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [metoda IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)