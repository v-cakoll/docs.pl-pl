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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e228cfbdade420c4d5248ffd417c6131083ee74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697280"
---
# <a name="corgcstattypes-enumeration"></a>COR_GC_STAT_TYPES — Wyliczenie
Określa statystyki, które mają być rejestrowane dla wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie Określa, które statystyki w [cor_gc_stats —](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktury mają zostać ustawiona przez [iclrgcmanager::getstats —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Rejestruje liczbę wyrzucania elementów bezużytecznych wykonywane dla każdej generacji.|  
|`COR_GC_MEMORYUSAGE`|Rekordy użycia i wyrzucania elementów kolekcji rozmiar statystyki pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [COR_GC_STATS, struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
