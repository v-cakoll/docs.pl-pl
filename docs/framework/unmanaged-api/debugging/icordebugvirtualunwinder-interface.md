---
title: "ICorDebugVirtualUnwinder — interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a09e9ccc-0b37-43e3-95c1-bc5fa7ee5f42
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 936df5c3d913a2ee5a1648906fb3ece2751d8ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvirtualunwinder-interface"></a>ICorDebugVirtualUnwinder — interfejs
Udostępnia metody, aby pomóc w odwijanie stosu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Nazwa|  
|------------|----------|  
|[GetContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-getcontext-method.md)|Pobiera bieżący kontekst tego unwinder.|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-next-method.md)|Przechodzi do kontekstu obiektu wywołującego.|  
  
## <a name="remarks"></a>Uwagi  
 Elementy członkowskie `ICorDebugVirtualUnwinder` interfejs jest implementowany przez debugera, aby pomóc w odwijanie stosu.  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z platformą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
