---
title: ICorDebugStackWalk — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk
helpviewer_keywords:
- ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb58040394d99ae0c5a10672946fa5a6ead5e751
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533419"
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk — Interfejs
Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Zwraca kontekst dla bieżącej ramki `ICorDebugStackWalk` obiektu.|  
|[SetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Zestawy `ICorDebugStackWalk` obiektu w bieżącym kontekście do prawidłowego kontekstu dla wątku.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.|  
|[GetFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Pobiera bieżące ramce `ICorDebugStackWalk` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
