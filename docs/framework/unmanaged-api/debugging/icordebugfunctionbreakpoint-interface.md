---
title: ICorDebugFunctionBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8403873fb7bc15e3109821bf738d7b68e20f878
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662689"
---
# <a name="icordebugfunctionbreakpoint-interface1"></a>ICorDebugFunctionBreakpoint Interface1
Rozszerza icordebugbreakpoint — interfejs w celu obsługi punktów przerwania w obrębie funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFunction, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|Pobiera wskaźnik interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w którym ustawiono punkt przerwania.|  
|[GetOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|Pobiera przesunięcie punktu przerwania w obrębie funkcji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
