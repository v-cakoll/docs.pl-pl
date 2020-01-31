---
title: ICorDebugRuntimeUnwindableFrame — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugUnwindableFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnwindableFrame
helpviewer_keywords:
- ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type:
- apiref
ms.openlocfilehash: 26b0c78d5b34b920decc8c549d90ba8147e3f323
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791920"
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame — Interfejs
Zapewnia obsługę niezarządzanych metod, które wymagają środowiska uruchomieniowego języka wspólnego (CLR), aby zwolnić ramkę.  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugRuntimeUnwindableFrame` to wyspecjalizowana wersja interfejsu ICorDebugFrame. Jest on używany przez metody niezarządzane, które wymagają wykonania przez środowisko uruchomieniowe ramki na bieżącym stosie. Istniejące konwencje odwinięcia nie działają, ponieważ nie używają kodu skompilowanego JIT. Gdy debuger widzi niewidocznyą ramkę, powinien użyć metody [ICorDebugStackWalk:: Next](icordebugstackwalk-next-method.md) , aby ją rozwinięcie, ale powinien wykonać inspekcję. Gdy debuger otrzymuje `ICorDebugRuntimeUnwindableFrame`, może wywołać metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) w celu pobrania kontekstu ramki.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
