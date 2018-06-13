---
title: Interfejs ICorDebugInstanceFieldSymbol
ms.date: 03/30/2017
ms.assetid: a4a8f259-b83a-4425-ae8b-72b067dbc0d9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82f6ccd43059f33a69b8b052f9efa34c4e4f2c1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417719"
---
# <a name="icordebuginstancefieldsymbol-interface"></a>Interfejs ICorDebugInstanceFieldSymbol
Reprezentuje informacje symbolu debugowania dla pola wystąpienia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getname-method.md)|Pobiera nazwę pola wystąpienia.|  
|[GetOffset, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getoffset-method.md)|Pobiera przesunięcie w bajtach tego pola wystąpienia w swojej klasie nadrzędnej.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-getsize-method.md)|Pobiera rozmiar w bajtach pole wystąpienia.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugInstanceFieldSymbol` Interfejs służy do pobierania informacji o symbolach debugowania dla pola wystąpienia.  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z platformą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugStaticFieldSymbol, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
