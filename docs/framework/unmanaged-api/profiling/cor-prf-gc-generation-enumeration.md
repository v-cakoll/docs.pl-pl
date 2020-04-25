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
ms.openlocfilehash: 0eb1f57e3505f9ce5bb8b831d30c3891e51097c3
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158570"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION — Wyliczenie
Identyfikuje Generowanie elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|Obiekt jest przechowywany jako generacja 0.|  
|`COR_PRF_GC_GEN_1`|Obiekt jest przechowywany jako generacja 1.|  
|`COR_PRF_GC_GEN_2`|Obiekt jest przechowywany jako generacja 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Obiekt jest przechowywany w stercie dużego obiektu.|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|Obiekt jest przechowywany w stercie przypiętych obiektów.|  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyrzucania elementów bezużytecznych zwiększa wydajność zarządzania pamięcią, dzieląc obiekty na generacji na podstawie wieku. Moduł wyrzucania elementów bezużytecznych obecnie używa trzech generacji, numerowanych 0, 1 i 2 oraz dwóch specjalnych segmentów sterty, jeden dla dużych obiektów i jeden dla przypiętych obiektów.
  
 Obiekty, których rozmiar przekracza wartość progową, są przechowywane w stercie dużego obiektu. Przypięte obiekty można przydzielić do sterty przypiętych obiektów, aby uniknąć kosztu związanego z przydzieleniem ich do normalnych stert. Inne przydziały, które zaczynają się od wygenerowania 0. Wszystkie obiekty istniejące po wyrzucaniu elementów bezużytecznych w generacji 0 są podwyższane do generacji 1. Obiekty istniejące po wyrzucaniu elementów bezużytecznych odbywają się w generacji 1.  
  
 Użycie generacji oznacza, że moduł zbierający elementy bezużyteczne musi współpracować z tylko podzbiorem przyznanych obiektów w dowolnym momencie.  
  
 `COR_PRF_GC_GENERATION` Wyliczenie jest używane przez strukturę [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Profilowanie — wyliczenia](profiling-enumerations.md)
