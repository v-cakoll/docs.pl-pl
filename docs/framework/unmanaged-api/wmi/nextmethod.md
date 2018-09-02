---
title: Funkcja NextMethod (niezarządzany wykaz interfejsów API)
description: Funkcja NextMethod pobiera Następna metoda w wyliczeniu.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d019c67849197cd24171ff607e60e9f08d5ff70
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43451626"
---
# <a name="nextmethod-function"></a>NextMethod — funkcja
Pobiera kolejna metoda wyliczenie, które zaczyna się od wywołania [BeginMethodEnumeration](beginmethodenumeration.md).  

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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lFlags`  
[in] Zastrzeżone. Ten parametr musi być 0.

`pName`  
[out] Wskaźnik, który wskazuje na `null` przed wywołaniem. Gdy funkcja zwróci wynik, nowy adres `BSTR` zawierający nazwę metody. 

`ppSignatureIn`  
[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) zawierający `in` parametrów dla metody. 

`ppSignatureOut`  
[out] Wskaźnik, który otrzymuje wskaźnik [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) zawierający `out` parametrów dla metody. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | 0x8004101d | Wystąpił brak wywołania [ `BeginEnumeration` ](beginenumeration.md) funkcji. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | Nie ma żadnych więcej właściwości w wyliczeniu. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.

Obiekt wywołujący rozpoczyna się sekwencja wyliczenie, wywołując [BeginMethodEnumeration](beginmethodenumeration.md) działać, a następnie wywołuje funkcję [NextMethod], aż funkcja zwróci `WBEM_S_NO_MORE_DATA`. Opcjonalnie, obiekt wywołujący zakończy sekwencję przez wywołanie metody [EndMethodEnumeration](endmethodenumeration.md). Obiekt wywołujący może rozwiązać niniejszą wyliczenia wcześnie, wywołując [EndMethodEnumeration](endmethodenumeration.md) w dowolnym momencie.

## <a name="example"></a>Przykład

Na przykład C++, zobacz [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) metody.

## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także  
[Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
