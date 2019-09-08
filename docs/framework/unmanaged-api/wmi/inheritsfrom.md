---
title: InheritsFrom — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja InheritsFrom określa, czy Klasa lub wystąpienie pochodzi od określonej klasy nadrzędnej.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c32c54ec56ea0fe4f4039ca6438a91338edbadb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798449"
---
# <a name="inheritsfrom-function"></a>InheritsFrom, funkcja
Określa, czy bieżąca Klasa lub wystąpienie pochodzi z określonej klasy nadrzędnej.

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`  
podczas Wskaźnik do wystąpienia [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .

`wszAncestor`  
podczas Nazwa klasy. `wszAncestor`musi wskazywać prawidłowy `LPCWSTR`.

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | 0 | Bieżący obiekt dziedziczy z `wszAncestor`.  |
| `WBEM_S_FALSE` | 1 | Bieżący obiekt nie dziedziczy po elemencie `wszAncestor`. |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszAncestor`jest `null`. |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemClassObject:: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
