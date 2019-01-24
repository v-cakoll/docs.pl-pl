---
title: COR_SEGMENT — Struktura
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55f1c0da651d786dfdcfda6a54ee1b29db35f3d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587742"
---
# <a name="corsegment-structure"></a>COR_SEGMENT — Struktura
Zawiera informacje o region pamięci w stosie zarządzanym.  
  
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
|`start`|Adres początkowy regionów pamięci.|  
|`end`|Końcowy adres regionu pamięci.|  
|`gen`|A [cordebuggenerationtypes —](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) składowej wyliczenia, która wskazuje Generowanie regionu pamięci.|  
|`heap`|Liczba sterty, w której znajduje się regionu pamięci. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_SEGMENTS` Struktury reprezentuje region pamięci w zarządzanym stosie.  `COR_SEGMENTS` obiekty są członkami [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) obiekt kolekcji, który jest wypełniana przez wywołanie metody [icordebugprocess5::enumerateheapregions —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.  
  
 `heap` Pole jest numer procesora, który odnosi się do sterty zgłaszane. Na stacji roboczej wyrzucania elementów modułów zbierających dzienniki jego zawsze ma wartość zero, ponieważ stacje robocze mają tylko jeden stercie wyrzucania elementów bezużytecznych. Dla moduły zbierające pamięci serwera jego wartość odpowiada procesora, której jest dołączona sterty. Należy pamiętać, że może istnieć więcej lub mniej wyrzucania elementów bezużytecznych sterty, niż rzeczywista procesorów ze względu na szczegóły implementacji moduł odśmiecania pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
