---
title: COR_GC_STAT_TYPES — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: d7e78dfc4beba67cc376b221d0cd49f7200f5d23
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501706"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES — Wyliczenie
Określa statystyki, które mają być rejestrowane w celu wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Uwagi  
 To Wyliczenie określa, które statystyki w strukturze [COR_GC_STATS](cor-gc-stats-structure.md) mają być ustawiane za pomocą metody [ICLRGCManager::](iclrgcmanager-getstats-method.md) getstatistics.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Rejestruje liczbę kolekcji elementów bezużytecznych wykonanych dla każdej generacji.|  
|`COR_GC_MEMORYUSAGE`|Rejestruje dane statystyczne dotyczące użycia pamięci i wyrzucania elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_GC_STATS, struktura](cor-gc-stats-structure.md)
- [Hosting — Wyliczenia](hosting-enumerations.md)
