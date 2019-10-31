---
title: GetObjectText — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja GetObjectText zwraca renderowanie tekstu obiektu w składni MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102453"
---
# <a name="getobjecttext-function"></a>GetObjectText, funkcja
Zwraca renderowanie tekstowe obiektu w składni Managed Object Format (MOF).

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lFlags`  
podczas Zwykle 0. Jeśli określono `WBEM_FLAG_NO_FLAVORS` (lub 0x1), kwalifikatory są uwzględniane bez informacji o propagacji lub wersji.

`pstrObjectText`   
określoną Wskaźnik do `null` przy wpisie. W przypadku powrotu, nowo przydzieloną `BSTR`, która zawiera wyrenderowanie obiektu przez składnię MOF.  

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby ukończyć tę operację. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .

Zwrócony tekst MOF nie zawiera wszystkich informacji o obiekcie, ale tylko wystarczające informacje dla kompilatora MOF, aby można było odtworzyć oryginalny obiekt. Na przykład nie są uwzględniane żadne kwalifikatory propagowane ani właściwości klasy nadrzędnej.

Następujący algorytm służy do rekonstruowania tekstu parametrów metody:

1. Parametry są ponownie sekwencjonowane w kolejności ich wartości identyfikatorów.
1. Parametry, które są określone jako `[in]` i `[out]`, są łączone w jeden parametr.
 
`pstrObjectText` musi być wskaźnikiem do `null`, gdy funkcja jest wywoływana; nie może wskazywać ciągu, który jest prawidłowy przed wywołaniem metody, ponieważ wskaźnik nie zostanie cofnięty.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils. idl  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
