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
ms.openlocfilehash: aabf3ac4e51280bd847d145e15ad804d514ede2c
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274011"
---
# <a name="cor_segment-structure"></a>COR_SEGMENT — Struktura
Zawiera informacje o regionie pamięci w zarządzanym stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`start`|Adres początkowy regionu pamięci.|  
|`end`|Adres końcowy regionu pamięci.|  
|`gen`|Element członkowski wyliczenia [CorDebugGenerationTypes —](cordebuggenerationtypes-enumeration.md) wskazujący generowanie regionu pamięci.|  
|`heap`|Numer sterty, w której znajduje się region pamięci. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_SEGMENTS` Struktura reprezentuje region pamięci w zarządzanym stosie.  `COR_SEGMENTS`obiekty są elementami członkowskimi obiektu kolekcji [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) , który jest wypełniany przez wywołanie metody [ICorDebugProcess5:: EnumerateHeapRegions —](icordebugprocess5-enumerateheapregions-method.md) .  
  
 `heap` Pole jest numerem procesora, który odnosi się do raportowanej sterty. W przypadku modułów bezużytecznych stacji roboczej jego wartość jest zawsze zerowa, ponieważ stacje robocze mają tylko jedną stertę odzyskiwania pamięci. W przypadku modułów wyrzucających elementy bezużyteczne serwera jego wartość odpowiada procesorowi, do którego jest dołączona sterta. Należy zauważyć, że może być więcej lub mniej sterty wyrzucania elementów bezużytecznych, ponieważ istnieją rzeczywiste procesory ze względu na szczegóły implementacji modułu wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
