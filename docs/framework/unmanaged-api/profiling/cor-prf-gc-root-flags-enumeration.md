---
title: "COR_PRF_GC_ROOT_FLAGS — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_ROOT_FLAGS
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords: COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e00f695edb94acbd54d6bd009ccd629aeec1b14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS — Wyliczenie
Wskazuje właściwość głównego kolekcji pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`COR_PRF_GC_ROOT_PINNING`|Katalog główny zapobiega wyrzucania elementów bezużytecznych przenoszenia obiektu.|  
|`COR_PRF_GC_ROOT_WEAKREF`|Katalog główny nie zapobiega wyrzucanie elementów bezużytecznych.|  
|`COR_PRF_GC_ROOT_INTERIOR`|Katalog główny odwołuje się do pola obiektu, a nie samego obiektu.|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|Głównego zapobiega wyrzucanie elementów bezużytecznych, jeśli liczba odwołanie do obiektu jest określoną wartość.|  
  
## <a name="remarks"></a>Uwagi  
 `COR_PRF_GC_ROOT_FLAGS`jest maską bitów udostępnia dodatkowe informacje o specjalne katalogów głównych. Niemniej jednak nie wszystkie certyfikaty główne są specjalne. Na przykład niektóre katalogów głównych nie są słabe odwołania, wewnętrznych wskaźników przypiętych lub zliczane odwołania. Dla tych certyfikatów głównych nie ma żadnych flag w celu przedstawienia. W związku z tym te metody, które używają tego wyliczenia, takich jak [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) metody send 0 flagi maski bitów, wskazujące, że wszystkie flagi są wyłączone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
