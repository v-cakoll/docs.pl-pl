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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c22e3c7c04a2b85723f1c0dba4543465faccab58
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745498"
---
# <a name="corprftransitionreason-enumeration"></a>COR_PRF_TRANSITION_REASON — Wyliczenie
Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub na odwrót.  
  
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
|`COR_PRF_TRANSITION_CALL`|Przejście wynika z wywołania do funkcji.|  
|`COR_PRF_TRANSITION_RETURN`|Przejście jest ze względu na powrót z funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku przejścia profiler otrzymuje [icorprofilercallback::managedtounmanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) lub [icorprofilercallback::unmanagedtomanagedtransition —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) wywołanie zwrotne, które udostępnia wartość `COR_PRF_TRANSITION_REASON` wyliczenie, aby wskazać przyczynę przejścia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
