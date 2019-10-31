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
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130852"
---
# <a name="icordebugilframe4-interface"></a>Interfejs ICorDebugILFrame4
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Zwraca listę zmiennych lokalnych dostępnych w bieżącej klatce.|  
|[GetCodeEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Zwraca kod, w którym jest uruchomiona ta ramka stosu.|  
|[GetLocalVariableEx, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Zwraca wartość zmiennej lokalnej w ramce IL.|  
  
## <a name="remarks"></a>Uwagi  
 Te metody oferują funkcje oprócz tych zapewnianych przez metody [EnumerateLocalVariables —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)i [GetLocalVariable —](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) . Każda metoda zawiera parametr `flags`, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowane przez żądanie ReJIT profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
