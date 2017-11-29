---
title: "Funkcja GetObjectText (niezarządzany wykaz interfejsów API)"
description: "Funkcja GetObjectText zwraca wartość tekstową renderowanie obiektu składnią MOF."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetObjectText
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetObjectText
helpviewer_keywords: GetObjectText function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 27e25a7ab7131f5b1c995c9367de6fe5a6fae592
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="getobjecttext-function"></a>Funkcja GetObjectText
Zwraca tekstową renderowanie obiektu w składni Managed Object Format (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lFlags`  
[in] Zazwyczaj 0. Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) określono kwalifikatorów są uwzględniane bez informacji o propagację lub wersji.

`pstrObjectText`   
[out] Wskaźnik do `null` zapisu. Zwraca na, nowo przydzielone `BSTR` zawierający renderowania składnią MOF obiektu.  

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci jest dostępna do wykonania operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::GetObjectText](https://msdn.microsoft.com/library/aa391448(v=vs.85).aspx) metody.

Tekst MOF zwrócił nie zawiera wszystkich informacji o obiekcie, ale tylko tych informacji dla kompilatora MOF można było ponownie utworzyć obiekt oryginalnego. Na przykład nie propagowany kwalifikatory lub właściwości klasy nadrzędnej są uwzględniane.

Następujący algorytm służy do rekonstrukcji tekst parametry metody:

1. Parametry są z ponownie określoną kolejnością według ich wartości identyfikatora.
1. Parametry, które są określone jako `[in]` i `[out]` są połączone w jeden parametr.
 
`pstrObjectText`musi być wskaźnikiem do `null` po wywołaniu funkcji; nie musi wskazywać na ciąg, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik myszy zostanie nie można cofnąć alokacji.

## <a name="requirements"></a>Wymagania  
**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
