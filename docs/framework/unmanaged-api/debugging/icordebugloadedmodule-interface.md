---
title: "ICorDebugLoadedModule — interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5cdc89ec81d76a3ce7d39a53e097745d6c9822f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule — interfejs
Udostępnia informacje na temat załadować modułu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseAddress — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Pobiera adres podstawowy załadować modułu.|  
|[GetName — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Pobiera nazwę załadować modułu.|  
|[GetSize — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Pobiera rozmiar w bajtach załadowanego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugLoadedModule` Interfejs jest implementowany przez debugera i jest używany przez środowisko CLR debugowania interfejsów można pobrać informacji o module załadowany z debugera.  
  
> [!NOTE]
>  Ten interfejs jest tylko dostępne z platformą .NET Native. W przypadku zastosowania tego interfejsu dla scenariuszy ICorDebug poza platformy .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
