---
title: Interfejs ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: deb300ced2ff7a116bd443c9a7b10dcc0b7955ac
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784533"
---
# <a name="icordebugassembly3-interface"></a>Interfejs ICorDebugAssembly3
Logicznie rozszerza interfejs ICorDebugAssembly w celu zapewnienia obsługi zestawów kontenerów i zawartych w nich zestawów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateContainedAssemblies, metoda](icordebugassembly3-enumeratecontainedassemblies-method.md)|Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.|  
|[GetContainerAssembly, metoda](icordebugassembly3-getcontainerassembly-method.md)|Zwraca zestaw kontenerów tego obiektu `ICorDebugAssembly3`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Interfejs jest dostępny tylko z .NET Native. Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
