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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f179e3b01d6c3b34dfa765565a0fc38d0ba867c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753695"
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS — Wyliczenie
Wskazuje właściwość kolekcji wyrzucania elementów katalogu głównego.  
  
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
|`COR_PRF_GC_ROOT_PINNING`|Katalog główny zapobiega wyrzucania elementów bezużytecznych z przeniesienia obiektu.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Katalog główny nie uniemożliwia wyrzucania elementów bezużytecznych.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Katalog główny odwołuje się do pola obiektu, a nie samego obiektu.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Katalog główny zapobiega wyrzucania elementów bezużytecznych, jeśli licznik odwołań obiektu jest określoną wartością.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_GC_ROOT_FLAGS` jest maską bitów, który zawiera dodatkowe informacje na temat specjalne katalogów głównych. Jednak nie wszystkie elementy główne są specjalne. Na przykład niektóre elementy główne nie są słabe odwołania, wskaźniki posługiwanie się nimi, przypiętych lub zliczonych odwołań. Takie elementy główne są nie flagi do przekazania. W związku z tym, w przypadku metod, które używają tego wyliczenia, takich jak [icorprofilercallback2::rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody wysyłania 0 maski bitów flag, wskazujący, że wszystkie flagi są wyłączone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
