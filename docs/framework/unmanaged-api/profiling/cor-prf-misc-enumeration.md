---
title: COR_PRF_MISC — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 7b8f2845589a8372f62c95ef1a82eae3ed602c1f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500835"
---
# <a name="cor_prf_misc-enumeration"></a>COR_PRF_MISC — Wyliczenie
Zawiera wartości stałe, które określają identyfikatory specjalne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|Domyślny identyfikator używany przez [ICorProfilerInfo:: GetModuleInfo —](icorprofilerinfo-getmoduleinfo-method.md) dla modułu, który nie został jeszcze dołączony do zestawu.|  
|`PROFILER_GLOBAL_CLASS`|Domyślny identyfikator klasy dla stałych globalnych, które nie należą do klasy.|  
|`PROFILER_GLOBAL_MODULE`|Domyślny identyfikator modułu dla obiektów globalnych, które nie należą do modułu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
