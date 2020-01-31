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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867218"
---
# <a name="cor_prf_gc_generation-enumeration"></a>COR_PRF_GC_GENERATION — Wyliczenie
Identyfikuje Generowanie elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`COR_PRF_GC_GEN_0`|Obiekt jest przechowywany jako generacja 0.|  
|`COR_PRF_GC_GEN_1`|Obiekt jest przechowywany jako generacja 1.|  
|`COR_PRF_GC_GEN_2`|Obiekt jest przechowywany jako generacja 2.|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|Obiekt jest przechowywany w stercie dużego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Moduł wyrzucania elementów bezużytecznych zwiększa wydajność zarządzania pamięcią, dzieląc obiekty na generacji na podstawie wieku. Moduł wyrzucania elementów bezużytecznych obecnie używa trzech generacji, numerowanych 0, 1 i 2, a także specjalnego segmentu sterty, który jest używany w przypadku dużych obiektów. Obiekty, których rozmiar jest większy niż określona wartość, są przechowywane w stercie dużego obiektu. Inne przydziały, które zaczynają się od wygenerowania 0. Wszystkie obiekty istniejące po wyrzucaniu elementów bezużytecznych w generacji 0 są podwyższane do generacji 1. Obiekty istniejące po wyrzucaniu elementów bezużytecznych odbywają się w generacji 1.  
  
 Użycie generacji oznacza, że moduł zbierający elementy bezużyteczne musi współpracować z tylko podzbiorem przyznanych obiektów w dowolnym momencie.  
  
 Wyliczenie `COR_PRF_GC_GENERATION` jest używane przez strukturę [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
