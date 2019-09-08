---
title: DeleteMethod — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja DeleteMethod usuwa określoną metodę z definicji klasy CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4db81c4c7e123eed82b3092912b8d871edb54618
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798661"
---
# <a name="deletemethod-function"></a>DeleteMethod, funkcja
Usuwa określoną metodę z definicji klasy CIM.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszName`  
podczas Nazwa metody do usunięcia z tabeli klas. `wszName`musi być wskaźnikiem prawidłowym `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | 0x80041002 | Określona metoda nie istnieje. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Za mało pamięci, aby ukończyć operację. |
| `WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |

## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) .

Usuwanie metody nie jest obsługiwane dla wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia modelu wspólnych informacji.

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
