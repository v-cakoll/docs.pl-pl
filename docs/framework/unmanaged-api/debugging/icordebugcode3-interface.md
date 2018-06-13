---
title: ICorDebugCode3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: febfe7df52a0c1f44cb156faf2da310d317e01a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411328"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 — Interfejs
Udostępnia metody, która rozszerza "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanych wartości zwracanej.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReturnValueLiveOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|Określony przesunięcia IL pobiera natywnego przesunięcia gdzie ma zostać umieszczony punkt przerwania, aby debuger można uzyskać wartości zwracanej przez funkcję.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
    
    
 [ICorDebugILFrame3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
