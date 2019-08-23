---
title: ICorDebugLoadedModule — interfejs
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a9da6aba61382381fc25fe70615976cd0e744ee1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910004"
---
# <a name="icordebugloadedmodule-interface"></a>ICorDebugLoadedModule — interfejs
Zawiera informacje o załadowanym module.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getbaseaddress-method.md)|Pobiera adres podstawowy załadowanego modułu.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getname-method.md)|Pobiera nazwę załadowanego modułu.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-getsize-method.md)|Pobiera rozmiar w bajtach załadowanego modułu.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugLoadedModule` Interfejs jest implementowany przez debuger i jest używany przez interfejsy debugowania CLR do uzyskiwania informacji o załadowanym module z debugera.  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
