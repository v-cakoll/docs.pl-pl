---
title: ICorDebugVirtualUnwinder — interfejs
ms.date: 03/30/2017
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
ms.openlocfilehash: 065f71e45c2a56dbaa16a45f70958ca3dea80c48
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790823"
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder — interfejs
Zapewnia metody pomagające w rozwinięcia stosu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Nazwa|  
|------------|----------|  
|[GetContext, metoda](icordebugvirtualunwinder-getcontext-method.md)|Pobiera bieżący kontekst tego elementu unwiatrer.|  
|[Next, metoda](icordebugvirtualunwinder-next-method.md)|Przechodzi do kontekstu obiektu wywołującego.|  
  
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

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
