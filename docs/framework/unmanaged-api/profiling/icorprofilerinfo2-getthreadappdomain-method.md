---
title: ICorProfilerInfo2::GetThreadAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32a69f948b936dd80ab364583dc2928778b34ba0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174411"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a>ICorProfilerInfo2::GetThreadAppDomain — Metoda
Pobiera identyfikator domeny aplikacji, w którym określony wątek jest w trakcie wykonywania kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 [in] Identyfikator, określając wątku.  
  
 `pAppDomainId`  
 [out] Wskaźnik do Identyfikatora domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
