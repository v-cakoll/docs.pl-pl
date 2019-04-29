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
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599042"
---
# <a name="corprftransitionreason-enumeration"></a>COR_PRF_TRANSITION_REASON — Wyliczenie
Wskazuje przyczynę przejścia z zarządzanego do kodu niezarządzanego lub na odwrót.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
