---
title: GetMethodOrigin — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetMethodOrigin określa klasę, w której jest zadeklarowana Metoda.
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
ms.openlocfilehash: 9cea7251353dae093f64448c8d84157917fa74c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798559"
---
# <a name="getmethodorigin-function"></a>GetMethodOrigin, funkcja
Określa klasę, w której jest zadeklarowana Metoda.

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
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszMethodName`  
podczas Nazwa metody dla obiektu, którego właścicielem jest żądana Klasa. 

`pstrClassName`  
określoną Odbiera nazwę klasy, która jest właścicielem metody.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Nie znaleziono określonej metody. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Co najmniej jeden parametr jest nieprawidłowy. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .

Ponieważ Klasa może dziedziczyć metody z co najmniej jednej klasy bazowej, deweloperzy często chcą określić klasę, w której zdefiniowana jest dana metoda.

Parametr nie może wskazywać prawidłowego `BSTR` przed `out` wywołaniem funkcji, ponieważ jest to parametr; ten wskaźnik nie jest cofany po powrocie funkcji. `pstrClassName`

## <a name="requirements"></a>Wymagania  
**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
