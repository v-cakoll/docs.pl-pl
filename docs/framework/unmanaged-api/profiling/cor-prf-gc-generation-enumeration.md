---
title: COR_PRF_GC_GENERATION — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15bd3ed8f1642e44ecf9c4df49feebd72eeac8c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590136"
---
# <a name="corprfgcgeneration-enumeration"></a>COR_PRF_GC_GENERATION — Wyliczenie
Identyfikuje generacji wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|Obiekt jest przechowywany jako generacji 0.|  
|`COR_PRF_GC_GEN_1`|Obiekt jest przechowywany jako generacji 1.|  
|`COR_PRF_GC_GEN_2`|Obiekt jest przechowywany jako generacji 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Obiekt jest przechowywany w stosie dużego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Moduł odśmiecania pamięci zwiększa wydajność zarządzania pamięcią, dzieląc obiektów na generacje, w oparciu o wieku. Moduł zbierający elementy bezużyteczne aktualnie używa trzy generacje, numerowane 0, 1 i 2 oraz segment specjalne sterty, który jest używany w przypadku dużych obiektów. Obiekty, których rozmiar przekracza określoną wartość są przechowywane w stosie dużego obiektu. Inne obiekty przydzielone zaczynają należące do generacji 0. Wszystkie obiekty znajdujące się po wyrzucanie elementów bezużytecznych występuje w generacji 0 są promowane do generacji 1. Obiekty, znajdujące się po wystąpieniu wyrzucania elementów bezużytecznych w generacji 1 są przenoszone do generacji 2.  
  
 Korzystanie z generacji oznacza, że moduł zbierający elementy bezużyteczne musi pracować tylko podzbiór przydzielone obiekty w dowolnym momencie.  
  
 `COR_PRF_GC_GENERATION` Wyliczenie jest używane przez [cor_prf_gc_generation_range —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
