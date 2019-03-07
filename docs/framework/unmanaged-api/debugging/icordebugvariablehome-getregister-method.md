---
title: ICorDebugVariableHome::GetRegister Method
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 73ab94765e1b76cb8521a0d546d6bc61384aad5f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480744"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome::GetRegister Method
Pobiera rejestr, który zawiera zmienną typu lokalizacji `VLT_REGISTER`oraz podstawowego rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRegister`  
 [out] Wartość wyliczenia cordebugregister —, która wskazuje rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER`oraz podstawowego rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca następujące wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Zmienna jest w rejestrze, wskazywanym przez `pRegister` argumentu.|  
|`E_FAIL`|Zmienna nie jest w rejestrze lub w lokalizacji rejestru powiązane z wątkiem.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [VariableLocationType, wyliczenie](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [ICorDebugVariableHome, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
