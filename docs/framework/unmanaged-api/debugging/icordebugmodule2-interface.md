---
title: ICorDebugModule2 Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 537023cf117477b54117799fc9ea62e894bb6591
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419143"
---
# <a name="icordebugmodule2-interface1"></a>ICorDebugModule2 Interface1
Służy jako logiczne rozszerzenia interfejsu ICorDebugModule.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyChanges, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|Stosuje zmiany w metadanych i zmian w kodzie języka pośredniego (MSIL) firmy Microsoft do uruchomionego procesu.|  
|[GetJITCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|Pobiera flagi sterujące kompilacji just-in-time (JIT) dla tego `ICorDebugModule2`.|  
|[ResolveAssembly, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|Usuwa zestaw odwołuje się token określonych metadanych.|  
|[SetJITCompilerFlags, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|Ustawia flagi sterujące kompilacji JIT to `ICorDebugModule2`.|  
|[SetJMCStatus, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|Ustawia stan tylko mój kod (JMC) wszystkich metod wszystkie klasy w tym `ICorDebugModule2` na określoną wartość, z wyjątkiem tych `pTokens` tablicy, która ustawia przeciwną wartość.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
