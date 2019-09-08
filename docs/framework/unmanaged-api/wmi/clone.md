---
title: Clone — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja klonowania zwraca nowy obiekt, który jest kompletnym klonem bieżącego.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5957f591dca7df30178660eb3fb074567c285715
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798705"
---
# <a name="clone-function"></a>Clone, funkcja
Zwraca nowy obiekt, który jest kompletnym klonem bieżącego obiektu.   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [out] IWbemClassObject**  ppCopy
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`ppCopy`  
określoną Nowy obiekt, który jest kompletną Lone `ptr`. Ten argument nie może `null` mieć wartości, Jeśli odbierze kopię bieżącego obiektu.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Wystąpił błąd ogólny. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `null`został określony jako parametr i nie jest dozwolony w tym użyciu. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało dostępnej pamięci, aby sklonować obiekt. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .

Sklonowany obiekt jest obiektem COM, który ma liczbę odwołań 1.

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
