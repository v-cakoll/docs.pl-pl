---
title: Funkcja GetObjectText (niezarządzany wykaz interfejsów API)
description: Funkcja GetObjectText zwraca wartość tekstową renderowanie obiektu składnią MOF.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4438b000a8ecf95949350d3665267276a1d959ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746498"
---
# <a name="getobjecttext-function"></a>GetObjectText, funkcja
Zwraca tekstową renderowanie obiektu w składni Managed Object Format (MOF).

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
[in] Ten parametr jest nieużywany.

`ptr`  
[in] Wskaźnik do [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) wystąpienia.

`lFlags`  
[in] Zazwyczaj 0. Jeśli `WBEM_FLAG_NO_FLAVORS` (lub 0x1) jest określony, kwalifikatory to wiąże się z nim informacje propagację lub wersja.

`pstrObjectText`   
[out] Wskaźnik do `null` przy uruchamianiu. Wróć na, nowo przydzielonego `BSTR` zawierający renderowanie składnią MOF obiektu.  

## <a name="return-value"></a>Wartość zwracana

Następujące wartości, które są zwracane przez tę funkcję, są zdefiniowane w *WbemCli.h* pliku nagłówkowego, lecz można również zdefiniować je jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Nie ma wystarczającej ilości pamięci jest dostępny do ukończenia tej operacji. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja zawija wywołanie do [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) metody.

Tekst MOF zwracany nie zawiera wszystkich informacji o obiekcie, ale tylko za mało informacji dla kompilatora MOF można było odtworzyć oryginalnego obiektu. Na przykład nie propagowany kwalifikatory ani właściwości klasy nadrzędnej, są uwzględniane.

Następującego algorytmu jest używana do rekonstrukcji tekst parametry metody:

1. Z ponownie parametry określoną kolejnością zgodnie z kolejnością ich wartości identyfikatora.
1. Parametry, które są określone jako `[in]` i `[out]` są łączone w pojedynczy parametr.
 
`pstrObjectText` musi być wskaźnikiem do `null` gdy wywoływana jest funkcja; nie musi wskazywać na ciąg, który jest prawidłowy, przed wywołaniem metody, ponieważ wskaźnik będzie nie można cofnąć alokacji.

## <a name="requirements"></a>Wymagania  
**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** WMINet_Utils.idl  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Usługi WMI i liczniki wydajności (niezarządzany wykaz interfejsów API)](index.md)
