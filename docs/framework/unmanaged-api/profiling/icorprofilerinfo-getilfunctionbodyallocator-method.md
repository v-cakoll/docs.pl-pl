---
title: "ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILFunctionBodyAllocator
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1feec20f0ddc4f6029490e06d4729b3fdaa7fa8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda
Pobiera interfejs, który udostępnia metody można przydzielić pamięci do zastosowania w przypadku zastępowaniu treści metody w kodzie języka pośredniego (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, w której znajduje się metody.  
  
 `ppMalloc`  
 [out] Wskaźnik do [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs, który udostępnia metody przydzielić pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Treści metody w kodzie MSIL musi znajdować się jako wirtualnego adresu względnego (RVA) względem załadować modułu, co oznacza, że jest on zgodny moduł w 4 GB. Aby ułatwić narzędzia wymienić treści metody, `GetILFunctionBodyAllocator` — metoda gwarantuje, że pamięć jest przydzielona w tym zakresie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
