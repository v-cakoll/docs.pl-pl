---
title: "ICorDebugRegisterSet — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet
helpviewer_keywords: ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 714f3d7839ce1d8b65405b6cb3c91d43f1db6642
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugregisterset-interface"></a>ICorDebugRegisterSet — Interfejs
Reprezentuje zestaw rejestry dostępne na komputerze, który jest w trakcie wykonywania kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetRegisters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregisters-method.md)|Pobiera wartość każdego rejestru (na komputerze, który jest aktualnie wykonywany kodu) określonym przez maska bitowa.|  
|[GetRegistersAvailable, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md)|Pobiera bit maski wskazujący, który rejestruje w tym `ICorDebugRegisterSet` są obecnie dostępne.|  
|[GetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getthreadcontext-method.md)|Pobiera kontekst bieżącego wątku.|  
|[SetRegisters, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setregisters-method.md)|Nie zaimplementowano dla platformy .NET Framework w wersji 2.0.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-setthreadcontext-method.md)|Nie zaimplementowano dla programu .NET Framework 2.0.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugRegisterSet` Interfejs obsługuje tylko 32-bitowych rejestrów. Użyj [ICorDebugRegisterSet2](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md) interfejsu na platformach takich jak IA-64, które wymagają dodatkowych rejestrów.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ICorDebugRegisterSet2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
