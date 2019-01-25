---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9db6b83e2feedd761b95dec455213051e37366e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684148"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder — interfejs
Dostarcza metody pomagające w wykonywania operacji odwijania stosu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Nazwa|  
|------------|----------|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Pobiera bieżący kontekst tego unwinder.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Przechodzi do obiektu wywołującego kontekstu.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera pomagające w wykonywania operacji odwijania stosu.  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z architekturą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
