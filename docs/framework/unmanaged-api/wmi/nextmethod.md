---
title: "Funkcja NextMethod (niezarządzany wykaz interfejsów API)"
description: "Funkcja NextMethod pobiera następnej metody w wyliczeniu."
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: NextMethod
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: NextMethod
helpviewer_keywords: NextMethod function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9b14424bb914be3ba127670e1b6490f79854d6e
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/15/2017
---
# <a name="nextmethod-function"></a>Funkcja NextMethod
Pobiera dalej w wyliczenie zaczyna się od wywołania metody [BeginMethodEnumeration](beginmethodenumeration.md).  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
[in] Ten parametr nie jest używana.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi wynosić 0.

`pName`  
[out] Wskaźnik, który wskazuje `null` przed wywołaniem. Gdy funkcja zwraca, nowy adres `BSTR` zawierający nazwę metody. 

`ppSignatureIn`  
[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) zawierający `in` parametry metody. 

`ppSignatureOut`  
[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx) zawierający `out` parametry metody. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w *WbemCli.h* pliku nagłówka, lub należy je zdefiniować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Nie znaleziono żadnych wywołanie [ `BeginEnumeration` ](beginenumeration.md) funkcji. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma żadnych więcej właściwości w wyliczeniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest zawijana wywołanie [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metody.

Obiekt wywołujący rozpoczyna sekwencji wyliczenie przez wywołanie metody [BeginMethodEnumeration](beginmethodenumeration.md) działać, a następnie wywołuje funkcję [NextMethod], dopóki funkcja zwraca `WBEM_S_NO_MORE_DATA`. Opcjonalnie, wywołujący zakończeniem sekwencji przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md). Obiekt wywołujący może zakończyć wyliczenia wcześniej przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.

## <a name="example"></a>Przykład

Na przykład C++, zobacz [IWbemClassObject::NextMethod](https://msdn.microsoft.com/library/aa391454(v=vs.85).aspx) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Liczniki wydajności (niezarządzany wykaz interfejsów API) i usługi WMI](index.md)
