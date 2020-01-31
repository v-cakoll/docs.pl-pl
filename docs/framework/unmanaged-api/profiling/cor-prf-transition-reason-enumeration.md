---
title: COR_PRF_TRANSITION_REASON — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867064"
---
# <a name="cor_prf_transition_reason-enumeration"></a>COR_PRF_TRANSITION_REASON — Wyliczenie
Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub odwrotnie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|Przejście jest spowodowane wywołaniem funkcji.|  
|`COR_PRF_TRANSITION_RETURN`|Przejście jest spowodowane zwracaniem z funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy następuje przejście, profiler otrzymuje wywołanie [ICorProfilerCallback:: ManagedToUnmanagedTransition —](icorprofilercallback-managedtounmanagedtransition-method.md) lub [ICorProfilerCallback:: UnmanagedToManagedTransition —](icorprofilercallback-unmanagedtomanagedtransition-method.md) , z którego każda zawiera wartość wyliczenia `COR_PRF_TRANSITION_REASON`, aby wskazać przyczynę przejścia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
