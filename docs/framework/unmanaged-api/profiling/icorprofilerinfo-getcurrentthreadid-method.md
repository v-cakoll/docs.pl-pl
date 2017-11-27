---
title: "ICorProfilerInfo::GetCurrentThreadID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCurrentThreadID
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 055a5f56f076cc29ca7ce5d45ecedd650e8f2f44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a>ICorProfilerInfo::GetCurrentThreadID — Metoda
Pobiera identyfikator bieżącego wątku, jeśli jest zarządzanego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThreadId`  
 [out] Wskaźnik do zwrócony identyfikator zarządzanego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli bieżący wątek jest wątku czasu wykonywania wewnętrznego lub innych niezarządzany wątek `GetCurrentThreadID` zwraca CORPROF_E_NOT_MANAGED_THREAD jako HRESULT i wartość `pThreadId` parametr będzie równy null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
