---
title: QualifierSet_EndEnumeration — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_EndEnumeration kończy Wyliczenie.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5a817174ec4c4e4407c19bb1d6d2d852d86dd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798322"
---
# <a name="qualifierset_endenumeration-function"></a>QualifierSet_EndEnumeration, funkcja
Kończy Wyliczenie rozpoczęte z wywołaniem funkcji [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`  
podczas Ten parametr jest nieużywany.

`ptr`   
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

## <a name="return-value"></a>Wartość zwracana

Następująca wartość zwrócona przez tę funkcję jest zdefiniowana w pliku nagłówkowym *WbemCli. h* lub można ją zdefiniować jako stałą w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .

To wywołanie jest zalecane, ale nie jest wymagane. Natychmiast zwalnia zasoby skojarzone z wyliczeniem.

## <a name="requirements"></a>Wymagania  

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
**Nagłówki** WMINet_Utils.idl  
  
**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
