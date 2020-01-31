---
title: COR_PRF_GC_ROOT_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
ms.openlocfilehash: 0210aca5698cd9c86979c13afd1e622b50d194df
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867190"
---
# <a name="cor_prf_gc_root_flags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS — Wyliczenie
Wskazuje Właściwość katalogu głównego wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|Katalog główny uniemożliwia przechodzenie obiektu przez wyrzucanie elementów bezużytecznych.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Element główny nie zapobiega wyrzucaniu elementów bezużytecznych.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Element główny odwołuje się do pola obiektu, a nie samego obiektu.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Katalog główny uniemożliwia wyrzucanie elementów bezużytecznych, jeśli liczba odwołań obiektu jest określona.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_GC_ROOT_FLAGS` jest maską bitów, która zawiera dodatkowe informacje na temat specjalnych katalogów głównych. Nie wszystkie elementy główne są jednak specjalne. Na przykład niektóre elementy główne nie są słabymi odwołaniami, wewnętrznymi wskaźnikami, przypiętymi lub zliczanymi odwołaniami. W przypadku takich elementów głównych nie ma flag do przekazania. W związku z tym metody używające tego wyliczenia, takie jak [ICorProfilerCallback2:: RootReferences2 —](icorprofilercallback2-rootreferences2-method.md) , wysyłają 0 dla flag maska bitów, wskazując, że wszystkie flagi są wyłączone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
