---
title: "ICorDebugStackWalk — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStackWalk
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStackWalk
helpviewer_keywords: ICorDebugStackWalk interface [.NET Framework debugging]
ms.assetid: 16d695e8-975d-431b-8421-e9e6c3e3f476
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 018ed69e52efd21ca25029284c70f1c8493d877f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstackwalk-interface"></a>ICorDebugStackWalk — Interfejs
Dostarcza metody pobierania zarządzanych metod, lub ramek, znajdujących się na stosie wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md)|Zwraca kontekst dla bieżącej ramki `ICorDebugStackWalk` obiektu.|  
|[SetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md)|Ustawia `ICorDebugStackWalk` bieżący kontekst obiektu do prawidłowego kontekstu wątku.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md)|Przenosi `ICorDebugStackWalk` obiektu do następnej ramki.|  
|[GetFrame, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getframe-method.md)|Pobiera bieżącą ramkę w `ICorDebugStackWalk` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
