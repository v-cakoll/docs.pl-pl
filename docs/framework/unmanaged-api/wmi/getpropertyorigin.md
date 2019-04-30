---
title: Funkcja GetPropertyOrigin (niezarządzany wykaz interfejsów API)
description: Funkcja GetPropertyOrigin Określa klasę, w którym zadeklarowany jest właściwością.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42e5cd6ee438b33fd07fd7c3242cc3c2a6513dd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723260"
---
# <a name="getpropertyorigin-function"></a>GetPropertyOrigin, funkcja

Określa klasę, w którym zadeklarowany jest właściwością.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a>Parametry

`vFunc`\
[in] Ten parametr jest nieużywany.

`ptr`\
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszMethodName`\
[in] Nazwa właściwości dla obiektu, którego klasa będąca właścicielem jest wymagana.

`pstrClassName`\
[out] Uzyskuje nazwę klasy, która jest właścicielem właściwości.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej właściwości. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) metody.

Ponieważ klasy mogą dziedziczyć właściwości jednego lub więcej klas bazowych, deweloperzy często chcemy określić właściwości, w którym zdefiniowano danej metody.

`pstrClassName` Parametru nie musi wskazywać na prawidłową `BSTR` przed wywołaniem funkcji, ponieważ jest to `out` parametru; ten wskaźnik nie cofnięto przydziału po powrocie z tej funkcji.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** WMINet_Utils.idl

**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)