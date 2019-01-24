---
title: Funkcja WritePropertyValue (niezarządzany wykaz interfejsów API)
description: Funkcja WritePropertyValue zapisuje bajty do właściwości.
ms.date: 11/06/2017
api_name:
- WritePropertyValue
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- WritePropertyValue
helpviewer_keywords:
- WritePropertyValue function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5a2588023309867694f344041f62be53cab9c37
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590123"
---
# <a name="writepropertyvalue-function"></a>WritePropertyValue — funkcja
Zapisuje określoną liczbę bajtów z właściwością identyfikowane przez dojście właściwości.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT WritePropertyValue (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] long                 lHandle,
   [in] long                 lNumBytes,
   [in] byte*                aData
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) wystąpienia.

`lHandle`  
[in] Liczba całkowita, która zawiera uchwyt, który identyfikuje tę właściwość. Uchwyt może być pobierany przez wywołanie [GetPropertyHandle](getpropertyhandle.md) funkcji.   

`lNumBytes`  
[in] Liczba bajtów zapisywanych do właściwości. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`pHandle`   
[out] Wskaźnik do tablicy typu byte, który zawiera dane.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Wystąpiła niezgodność typów. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::WritePropertyValue](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-writepropertyvalue) metody.

Ta funkcja służy do ciągu i wszystkie inne non -`DWORD` lub -`QWORD` danych.

W przypadku wartości właściwości typu `lNumBytes` musi być prawidłowe dane rozmiar określony typ właściwości. Wartości właściwości ciągu `lNumBytes` musi mieć długość określonego ciągu w bajtach i ciągu musi być nawet długości w bajtach wraz z występować znak zakończenia o wartości null.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
