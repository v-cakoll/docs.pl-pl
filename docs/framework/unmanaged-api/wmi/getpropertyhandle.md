---
title: Funkcja GetPropertyHandle (niezarządzany wykaz interfejsów API)
description: Funkcja GetPropertyHandle zwraca uchwyt unikatowy tej właściwości tożsamości.
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
ms.openlocfilehash: 103e81dfa0e455157cfce5914b711347b15b578d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="getpropertyhandle-function"></a>Funkcja GetPropertyHandle
Zwraca unikatowy dojścia identyfikujący właściwości.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPropertyHandle (
   [in] int                  vFunc, 
   [in] IWbemObjectAccess*   ptr, 
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) wystąpienia.

`wszPropertyName`  
[in] Zerem ciąg kodowany w formacie UTF16 characaters, który zawiera nazwę właściwości.   

`pType`  
[out] Wskaźnik do [ `CIMTYPE` ](https://msdn.microsoft.com/library/aa386309(v=vs.85).aspx) element członkowski wyliczenia, który reprezentuje typ CIM właściwości.

`pHandle`   
[out] Wskaźnik do liczba całkowita, która zawiera dojście właściwości.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określona nazwa właściwości nie został znaleziony. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_NOT_SUPPORTED` | 0x8004100c | Żądana właściwość jest typu są `CIM_OBJECT` lub `CIM_ARRAY`. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetPropertyHandle](https://msdn.microsoft.com/library/aa391771(v=vs.85).aspx) metody.

Przy użyciu tego uchwytu do identyfikowania właściwości, korzystając z [IWbemObjectAccess](https://msdn.microsoft.com/library/aa391770(v=vs.85).aspx) metod do odczytu lub zapisu wartości właściwości.

Uchwyty można pobrać właściwości wszystkich typów danych innych niż `CIM_OBJECT` i `CIM_ARRAY`. Zwracane pracy uchwytów we wszystkich wystąpieniach klasy.

## <a name="requirements"></a>Wymagania  
**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
