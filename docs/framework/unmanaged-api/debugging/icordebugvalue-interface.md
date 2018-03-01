---
title: ICorDebugValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3464b4ad963b2fe764cefc5868440b7748f8c4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue-interface1"></a>ICorDebugValue Interface1
Reprezentuje wartość w debugowanym procesie. Wartość może być wartość zapisu lub odczytu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Ta metoda nie jest obecnie zaimplementowana.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Pobiera adres tego `ICorDebugValue` obiektu, który jest w trakcie debugowania.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Pobiera rozmiar w bajtach to `ICorDebugValue` obiektu.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Pobiera pierwotny typ `ICorDebugValue` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc prawo własności obiektu wartość jest przekazywany, gdy jest zwracany. Odbiorca jest odpowiedzialny za usuwanie odwołań z obiektu po jego zakończeniu z obiektem.  
  
 W zależności od tego, gdzie wartość została pobrana z wartość może pozostają w mocy po wznowieniu procesu. Tak, ogólnie rzecz biorąc, wartość nie powinna być przechowywana przez wywołanie elementu [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
    
    
    
 [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
