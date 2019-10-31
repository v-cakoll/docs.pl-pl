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
ms.openlocfilehash: b0fbc462283ef1577de8100e60fd09caa53db539
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131912"
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
 To Wyliczenie określa, które statystyki w strukturze [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) mają być ustawiane za pomocą metody [ICLRGCManager::](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) getstatistics.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Rejestruje liczbę kolekcji elementów bezużytecznych wykonanych dla każdej generacji.|  
|`COR_GC_MEMORYUSAGE`|Rejestruje dane statystyczne dotyczące użycia pamięci i wyrzucania elementów bezużytecznych.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_GC_STATS, struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
