---
title: "ICorProfilerCallback::JITInlining — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining — Metoda
Powiadamia profilera kompilatora just-in-time (JIT) o zbliżającym się Wstawianie funkcji z inną funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a>Parametry  
 `callerId`  
 [in] Identyfikator funkcji, do którego `calleeId` zostanie wstawiona funkcja.  
  
 `calleeId`  
 [in] Identyfikator funkcji do wstawienia.  
  
 `pfShouldInline`  
 [out] `true` do wstawiania występuje; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Można ustawić profilera `pfShouldInline` do `false` zapobiegające `calleeId` funkcji wstawiane do `callerId` funkcji. Ponadto profilera globalnie można wyłączyć wbudowanego wstawiania za pomocą wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 Dodaje funkcje wbudowane nie wywołuj zdarzenia o. W związku z tym należy ustawić profilera `pfShouldInline` do `false` w celu uzyskania dokładnych Wykres wywołań. Ustawienie `pfShouldInline` do `false` będzie miało wpływ na wydajność, ponieważ wstawiania wbudowanego zwykle zwiększa szybkość i zmniejsza liczbę odrębne zdarzenia kompilacji JIT wstawionego metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
