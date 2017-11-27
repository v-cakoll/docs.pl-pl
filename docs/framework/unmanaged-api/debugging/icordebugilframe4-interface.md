---
title: Interfejs ICorDebugILFrame4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame4
api_location: mscordbi.dll
api_type: COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80b42a2ed4e93fd5e4c662bab34b111fe0757890
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilframe4-interface"></a>Interfejs ICorDebugILFrame4
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu w języku pośrednim (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodzie dodanym w ReJIT Instrumentacji profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Metoda EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Zwraca listę zmiennych lokalnych dostępnych w bieżącej ramki.|  
|[Metoda GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Zwraca kod, który działa tej ramki stosu.|  
|[Metoda GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Zwraca wartość zmiennej lokalnej w ramce IL.|  
  
## <a name="remarks"></a>Uwagi  
 Te metody oferują funkcje oprócz udostępniane przez [EnumerateLocalVariables](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), i [GetLocalVariable](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody. Każda metoda obejmuje `flags` parametr, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowany przez profiler ReJIT żądanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
