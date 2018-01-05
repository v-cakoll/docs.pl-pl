---
title: "Funkcja WritePropertyValue (niezarządzany wykaz interfejsów API)"
description: "Funkcja WritePropertyValue zapisuje bajty w właściwości."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: WritePropertyValue
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: WritePropertyValue
helpviewer_keywords: WritePropertyValue function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7221c9e0f1cb49ab0e27130ce69c0527ba903148
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="writepropertyvalue-function"></a>Funkcja WritePropertyValue
Zapisuje określoną liczbę bajtów do właściwości identyfikowany przez dojście właściwości.

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
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) wystąpienia.

`lHandle`  
[in] Liczba całkowita, która zawiera dojście, która identyfikuje tę właściwość. Dojście można pobranej poprzez wywołanie [GetPropertyHandle](getpropertyhandle.md) funkcji.   

`lNumBytes`  
[in] Liczba bajtów zapisywanych właściwości. Zobacz [uwagi](#remarks) sekcji, aby uzyskać więcej informacji.

`pHandle`   
[out] Wskaźnik do tablicy typu byte, który zawiera dane.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_TYPE_MISMATCH` | 0x80041005 | Wystąpiła niezgodność typów. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::WritePropertyValue](https://msdn.microsoft.com/library/aa391783(v=vs.85).aspx) metody.

Użyj tej funkcji, aby ustawić parametry i wszystkich innych firm innych niż firma`DWORD` lub z systemem innym niż-`QWORD` danych.

Dla typu wartości właściwości `lNumBytes` musi być prawidłowe dane rozmiar określony typ właściwości. Wartości właściwości ciągu `lNumBytes` musi mieć długość określonego ciągu w bajtach i ciągu musi być parzysta długości w bajtach i znajdować się znakiem null zakończenia.

## <a name="requirements"></a>Wymagania  
**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
