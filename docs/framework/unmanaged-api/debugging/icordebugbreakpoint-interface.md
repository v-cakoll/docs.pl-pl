---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a>ICorDebugBreakpoint Interface1
Reprezentuje punkt przerwania w funkcji lub punkt czujki na wartość.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Activate — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Ustawia stan aktywny `ICorDebugBreakpoint`.|  
|[IsActive — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Pobiera wartość wskazującą, czy to `ICorDebugBreakpoint` jest aktywny.|  
  
## <a name="remarks"></a>Uwagi  
 Punkty przerwania nie obsługują bezpośrednio wyrażenia warunkowego. W razie potrzeby takich funkcji debugera musi implementować on nad `ICorDebugBreakpoint`.  
  
 Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
