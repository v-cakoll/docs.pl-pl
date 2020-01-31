---
title: ICorDebugThread3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791392"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 — Interfejs
Udostępnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateStackWalk, metoda](icordebugthread3-createstackwalk-method.md)|Tworzy obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.|  
|[GetActiveInternalFrames, metoda](icordebugthread3-getactiveinternalframes-method.md)|Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) obiektów) na stosie.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugThread3` jest logicznym rozszerzeniem interfejsu ICorDebugThread.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
