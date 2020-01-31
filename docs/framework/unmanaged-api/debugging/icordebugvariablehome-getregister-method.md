---
title: 'ICorDebugVariableHome:: getregister — Metoda'
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
ms.openlocfilehash: 396dd9c017fca6dc7037b43355ba7f726d7390ea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790990"
---
# <a name="icordebugvariablehomegetregister-method"></a>ICorDebugVariableHome:: getregister — Metoda
Pobiera rejestr zawierający zmienną z typem lokalizacji `VLT_REGISTER`i podstawową rejestracją dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRegister`  
 określoną Wartość wyliczenia CorDebugRegister —, która wskazuje rejestr dla zmiennej z typem lokalizacji `VLT_REGISTER`i podstawowy rejestr dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca następujące wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Zmienna znajduje się w rejestrze wskazanym przez argument `pRegister`.|  
|`E_FAIL`|Zmienna nie znajduje się w rejestrze ani w lokalizacji względnej do rejestracji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [VariableLocationType, wyliczenie](variablelocationtype-enumeration.md)
- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)
