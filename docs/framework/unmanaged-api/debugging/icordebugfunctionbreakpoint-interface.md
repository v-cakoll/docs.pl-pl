---
title: ICorDebugFunctionBreakpoint, interfejs
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
ms.openlocfilehash: 5e3804335bacefad61c4f521ea1ef1444b7b1fed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777705"
---
# <a name="icordebugfunctionbreakpoint-interface"></a>ICorDebugFunctionBreakpoint, interfejs

Rozszerza interfejs ICorDebugBreakpoint w celu obsługi punktów przerwania w funkcjach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFunction, metoda](icordebugfunctionbreakpoint-getfunction-method.md)|Pobiera wskaźnik interfejsu do elementu ICorDebugFunction, który odwołuje się do funkcji, w której jest ustawiony punkt przerwania.|  
|[GetOffset, metoda](icordebugfunctionbreakpoint-getoffset-method.md)|Pobiera przesunięcie punktu przerwania w funkcji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
