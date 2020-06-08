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
ms.openlocfilehash: e890c62a54654e86bb4a825613807efe142c8d5a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500744"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|Przejście jest spowodowane wywołaniem funkcji.|  
|`COR_PRF_TRANSITION_RETURN`|Przejście jest spowodowane zwracaniem z funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy następuje przejście, profiler otrzymuje wywołanie [ICorProfilerCallback:: ManagedToUnmanagedTransition —](icorprofilercallback-managedtounmanagedtransition-method.md) lub [ICorProfilerCallback:: UnmanagedToManagedTransition —](icorprofilercallback-unmanagedtomanagedtransition-method.md) , z którego każda zawiera wartość `COR_PRF_TRANSITION_REASON` wyliczenia, aby wskazać przyczynę przejścia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
