---
title: ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cd66a895f99d62e8deaa45afab12d963aee2901
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109125"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator — Metoda
Pobiera interfejs, który udostępnia metodę, aby przydzielić pamięć do użytku z zastępowaniu treści metody w kodzie języka intermediate language (MSIL) firmy Microsoft.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identyfikator modułu, w której znajduje się metody.  
  
 `ppMalloc`  
 [out] Wskaźnik do [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interfejs, który udostępnia metodę w celu przydzielenia pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Treści metody w kodzie MSIL muszą znajdować się jako względnych adresów wirtualnych (RVA) względem załadowanym module, co oznacza, że jest zgodna z modułu w 4 GB. Aby ułatwić narzędzie wymienić treści metody `GetILFunctionBodyAllocator` metoda zapewnia, że pamięć jest przydzielany w tym zakresie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
