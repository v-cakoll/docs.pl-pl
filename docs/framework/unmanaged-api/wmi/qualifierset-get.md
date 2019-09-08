---
title: QualifierSet_Get — funkcja (niezarządzana dokumentacja interfejsu API)
description: Funkcja QualifierSet_Get pobiera nazwany kwalifikator.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 751694985248346187eff016ef7a4a8054cb1212
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798312"
---
# <a name="qualifierset_get-function"></a>QualifierSet_Get, funkcja
Pobiera określony kwalifikator nazwany.  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a>Parametry

`vFunc`   
podczas Ten parametr jest nieużywany.

`ptr`   
podczas Wskaźnik do wystąpienia [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .

`wszName`   
podczas Nazwa kwalifikatora, którego żądano wartości.

`lFlags`   
podczas Rezerwacj. Ten parametr musi być równy 0.

`pVal`   
określoną Po pomyślnym wykonaniu prawidłowy typ i wartość kwalifikatora. Jeśli funkcja się nie powiedzie `VARIANT` , wskazywane `pVal` przez nie jest modyfikowane. Jeśli ten parametr ma `null`wartość, parametr jest ignorowany.

`plFlavor`   
określoną Wskaźnik do LONG, który odbiera bity wersji kwalifikatora dla żądanego kwalifikatora. Jeśli informacje o wersji nie są potrzebne, ten parametr może `null`być. 

## <a name="return-value"></a>Wartość zwracana

Następujące wartości zwracane przez tę funkcję są zdefiniowane w pliku nagłówkowym *WbemCli. h* lub można je definiować jako stałe w kodzie:

|Stała  |Wartość  |Opis  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | Parametr jest nieprawidłowy. |
|`WBEM_E_NOT_FOUND` | 0x80041002 | Określony kwalifikator nie istnieje. |
|`WBEM_S_NO_ERROR` | 0 | Wywołanie funkcji zakończyło się pomyślnie.  |
  
## <a name="remarks"></a>Uwagi

Ta funkcja otacza wywołanie metody [IWbemQualifierSet:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .

## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** WMINet_Utils.idl  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [WMI i liczniki wydajności (niezarządzana dokumentacja interfejsu API)](index.md)
