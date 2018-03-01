---
title: "COR_SEGMENT — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a>COR_SEGMENT — Struktura
Zawiera informacje na temat obszar pamięci sterty zarządzanej.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;            
    CORDB_ADDRESS end;              
    CorDebugGenerationTypes gen;    
    ULONG heap;                     
} COR_SEGMENT;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`start`|Adres początkowy obszaru pamięci.|  
|`end`|Końcowy adres regionu pamięci.|  
|`gen`|A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) element członkowski wyliczenia wskazująca generacji regionu pamięci.|  
|`heap`|Liczba stosu, w której znajduje się obszar pamięci. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_SEGMENTS` Struktury reprezentuje obszar pamięci sterty zarządzanej.  `COR_SEGMENTS`obiekty są członkami [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiektu kolekcji, która jest wypełniana przez wywołanie metody[ICorDebugProcess5::EnumerateHeapRegions](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.  
  
 `heap` Pole jest numer procesora, co odpowiada sterty zgłaszają. Moduły zbierające elementy bezużyteczne stacji roboczej jego wartość jest zawsze zero, ponieważ stacje robocze mają tylko jeden sterty kolekcji pamięci. Dla modułów zbierających dane pamięci serwera jego wartość odpowiada procesora, której jest dołączona sterty. Należy pamiętać, że może istnieć więcej lub mniej pamięci sterty, niż rzeczywista procesory z powodu szczegóły implementacji moduł garbage collector.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
