---
title: Funkcja GetMethodOrigin (niezarządzany wykaz interfejsów API)
description: Funkcja GetMethodOrigin Określa klasę, w którym zadeklarowany jest metodą.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b21e08d3bf6845b9fc44d5a5edef0ea39b91da5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746533"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin, funkcja
Określa klasę, w którym zadeklarowany jest metodą.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`wszMethodName`  
[in] Nazwa metody dla obiektu, którego klasa będąca właścicielem jest wymagana. 

`pstrClassName`  
[out] Uzyskuje nazwę klasy, która jest właścicielem metody.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie można odnaleźć określonej metody. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Jeden lub więcej parametrów są nieprawidłowe. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) metody.

Ponieważ klasa może dziedziczyć metody z jednego lub więcej klas bazowych, deweloperzy często chcą określić klasę, w którym zdefiniowano danej metody.

`pstrClassName` Parametru nie musi wskazywać na prawidłową `BSTR` przed wywołaniem funkcji, ponieważ jest to `out` parametru; ten wskaźnik nie cofnięto przydziału po powrocie z tej funkcji.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
