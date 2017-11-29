---
title: "ICorProfilerInfo::BeginInprocDebugging — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.BeginInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c7c0b3c0a20c98b9ca2e5dd5ea51053008e415a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging — Metoda
Inicjuje obsługę debugowania w procesie. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fThisThreadOnly`  
 [in] Ta wartość `true` zainicjować obsługę debugowania tylko bieżącego wątku; ustaw ją na `false` zainicjować obsługę debugowania dla wszystkich wątków.  
  
 `pdwProfilerContext`  
 [out] Wskaźnik do zwrócona wartość, która identyfikuje sesji debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Usług debugowania środowiska CLR obsługiwane ograniczony w trakcie debugowania w wersji systemu .NET Framework 1.0 i 1.1. Debugowanie w trakcie włączone profiler do używania kontroli części interfejsu API debugowania. Jednak ze względu na opinie klientów, w trakcie debugowania ma został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestaw funkcji, która jest zgodna z interfejsu API profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersja platformy .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
