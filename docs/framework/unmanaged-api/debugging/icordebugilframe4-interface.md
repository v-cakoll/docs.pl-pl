---
title: Interfejs ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb3f55a8a0ddff6c3202d15dc4704d443cabb44d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54656950"
---
# <a name="icordebugilframe4-interface"></a>Interfejs ICorDebugILFrame4
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Udostępnia metody, które umożliwiają dostęp do zmiennych lokalnych i kod w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy narzędzie debuger ma dostęp do zmiennych i kodzie dodanym w profilerze ReJIT instrumentacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Zwraca listę zmiennych lokalnych dostępnych w bieżącej ramki.|  
|[GetCodeEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Zwraca kod, który działa tej ramki stosu.|  
|[GetLocalVariableEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Zwraca wartość zmiennej lokalnej w ramce IL.|  
  
## <a name="remarks"></a>Uwagi  
 Te metody oferują funkcje oprócz tego są udostępniane przez [enumeratelocalvariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode —](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), i [getlocalvariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody. Każda metoda obejmuje `flags` parametr, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowany przez profiler ReJIT żądanie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
