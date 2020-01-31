---
title: 'ICorDebugVariableHome:: GetOffset — Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: a6f93ec3c7ffe415c41dcf094dbde2f0a08969f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791000"
---
# <a name="icordebugvariablehomegetoffset-method"></a>ICorDebugVariableHome:: GetOffset — Metoda
Pobiera przesunięcie z rejestru podstawowego dla zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pOffset`  
 określoną Przesunięcie od podstawowego rejestru.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca następujące wartości:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Zmienna znajduje się w lokalizacji pamięci względnej do rejestracji.|  
|`E_FAIL`|Zmienna nie znajduje się w lokalizacji pamięci względnej do rejestracji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)
