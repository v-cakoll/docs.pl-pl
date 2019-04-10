---
title: ICorDebugDataTarget3 — interfejs
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3b0d67d390931cc92c0b6a1320f66545517cde3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223046"
---
# <a name="icordebugdatatarget3-interface"></a>ICorDebugDataTarget3 — interfejs
Rozszerza logicznie [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu, aby podać informacje o załadowanych modułów.  
  
## <a name="method"></a>Metoda  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetLoadedModules, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|Pobiera listę modułów, które zostały załadowane do tej pory.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z architekturą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
