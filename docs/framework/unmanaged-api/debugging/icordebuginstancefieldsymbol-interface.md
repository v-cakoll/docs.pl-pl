---
title: ICorDebugInstanceFieldSymbol, interfejs
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
ms.openlocfilehash: 41258b0eeed5fbf8ab86546f74073f8eeaa3085c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777525"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>ICorDebugInstanceFieldSymbol, interfejs
Przedstawia informacje o symbolu debugowania dla pola wystąpienia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName, metoda](icordebuginstancefieldsymbol-getname-method.md)|Pobiera nazwę pola wystąpienia.|  
|[GetOffset, metoda](icordebuginstancefieldsymbol-getoffset-method.md)|Pobiera przesunięcie w bajtach tego pola wystąpienia w jego klasie nadrzędnej.|  
|[GetSize, metoda](icordebuginstancefieldsymbol-getsize-method.md)|Pobiera rozmiar w bajtach pola wystąpienia.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugInstanceFieldSymbol` służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugStaticFieldSymbol, interfejs](icordebugstaticfieldsymbol-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
