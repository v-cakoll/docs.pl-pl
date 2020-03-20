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
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179286"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`start`|Adres początkowy regionu pamięci.|  
|`end`|Adres końcowy regionu pamięci.|  
|`gen`|A [CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) element członkowski wyliczenia, który wskazuje generowanie regionu pamięci.|  
|`heap`|Numer sterty, w którym znajduje się region pamięci. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura `COR_SEGMENTS` reprezentuje region pamięci w zarządzanym stosie.  `COR_SEGMENTS`obiekty są członkami obiektu kolekcji [ICorDebugHeapRegionEnum,](icordebugheapsegmentenum-interface.md) który jest wypełniany przez [wywołanie metody ICorDebugProcess5::EnumerateHeapRegions.](icordebugprocess5-enumerateheapregions-method.md)  
  
 To `heap` pole jest numerem procesora, który odpowiada zgłoszonemu stercie. Dla modułów zbierających elementy bezużyteczne stacji roboczej jego wartość jest zawsze równa zero, ponieważ stacje robocze mają tylko jedną stertę wyrzucania elementów bezużytecznych. W przypadku modułów zbierających elementy bezużyteczne serwera jego wartość odpowiada procesorowi, do którym jest dołączona sterta. Należy zauważyć, że może być więcej lub mniej sterty wyrzucania elementów bezużytecznych niż istnieją rzeczywiste procesory ze względu na szczegóły implementacji modułu zbierającego elementy bezużyteczne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugging](index.md)
