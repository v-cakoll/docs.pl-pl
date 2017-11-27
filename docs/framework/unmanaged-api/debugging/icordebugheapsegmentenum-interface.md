---
title: "ICorDebugHeapSegmentEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHealRegionEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapSegmentEnum
helpviewer_keywords: ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 20fc1b9d-e228-4107-bd76-53934c1724b9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5ca82e888ba078fcb8b855f5286bc14f970d64ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapsegmentenum-interface"></a>ICorDebugHeapSegmentEnum — Interfejs
Zawiera moduł wyliczający dla obszarów pamięci zarządzanej sterty. Ten interfejs jest podklasą klasy interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md)|Pobiera określoną liczbę [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień, które zawierają informacje na temat regionów sterty zarządzanej.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugHeapSegmentEnum` Interfejsu implementuje interfejs ICorDebugEnum.  
  
 `ICorDebugHeapSegmentEnum` Wystąpień jest wypełniana [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) wystąpień przez wywołanie metody [ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody. [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) mogą być wyliczane obiektów w kolekcji, wywołując [ICorDebugHeapSegmentEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-next-method.md) metody.  
  
 `ICorDebugHeapSegmentEnum` Obiektu kolekcji wylicza wszystkie regiony pamięci, które mogą zawierać obiektów zarządzanych, ale nie gwarantuje, że obiekty zarządzane rzeczywiście znajdują się w regionach. Mogą one obejmować informacji o regionach pamięci pusty lub zastrzeżone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
