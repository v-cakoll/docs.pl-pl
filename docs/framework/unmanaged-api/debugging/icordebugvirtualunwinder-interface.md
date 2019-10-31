---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 532052aa4f869861fbdb40ba0126bfd800eba942
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121876"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder — interfejs
Zapewnia metody pomagające w rozwinięcia stosu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Nazwa|  
|------------|----------|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Pobiera bieżący kontekst tego elementu unwiatrer.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Przechodzi do kontekstu obiektu wywołującego.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy członkowskie interfejsu `ICorDebugVirtualUnwinder` są implementowane przez debuger, aby pomóc w rozwinięcia stosu.  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
