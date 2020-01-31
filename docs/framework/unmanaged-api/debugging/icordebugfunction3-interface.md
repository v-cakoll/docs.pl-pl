---
title: Interfejs ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: 7ef983c2f0785cb97baf8ba1ad3483b46c08af9a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788661"
---
# <a name="icordebugfunction3-interface"></a>Interfejs ICorDebugFunction3
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Logicznie rozszerza interfejs ICorDebugFunction w celu zapewnienia dostępu do kodu z żądania ReJIT.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode, metoda](icordebugfunction3-getactiverejitrequestilcode-method.md)|Pobiera wskaźnik interfejsu do [ICorDebugILCode](icordebugilcode-interface.md) zawierającego Il z aktywnego żądania ReJIT.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
- [ReJIT: Przewodnik po poradniku](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
