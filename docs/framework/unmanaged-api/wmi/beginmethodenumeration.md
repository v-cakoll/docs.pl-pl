---
title: BeginMethodEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja BeginMethodEnumeration rozpoczyna Wyliczenie metod obiektu.
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a7b93bacabdfdd0551418644a7d9a4b1643c3d9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798762"
---
# <a name="beginenumeration-function"></a>BeingEnumeration, funkcja
Rozpoczyna Wyliczenie metod dostępnych dla obiektu.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`lEnumFlags`  
podczas Zero (0) dla wszystkich metod lub flagę, która określa zakres wyliczenia. Poniższe flagi są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | Ogranicz Wyliczenie do metod, które są zdefiniowane w samej klasie. |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | Ogranicz Wyliczenie do właściwości, które są dziedziczone z klas bazowych. |

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lEnnumFlags`jest różna od zera i nie jest jedną z określonych flag. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .

To wywołanie metody jest obsługiwane tylko wtedy, gdy bieżący obiekt jest definicją klasy. Manipulowanie metodami nie jest dostępne ze wskaźników [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) , które wskazują wystąpienia. Kolejność, w jakiej metody są wyliczane, gwarantuje, że jest niezmienna dla danego wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
