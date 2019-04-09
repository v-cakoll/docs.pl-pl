---
title: ICorProfilerInfo::GetCodeInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d069446ecb0b630870f0d2c9c4bdc23232c40c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120695"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo — Metoda
Pobiera zakres kodu natywnego skojarzony z identyfikatorem określonej funkcji.  
  
 Ta metoda jest przestarzała. Użyj [icorprofilerinfo2::getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, z którą jest skojarzony kod macierzysty.  
  
 `pStart`  
 [out] Wskaźnik do tablicy bajtów, które tworzą natywny kod funkcji.  
  
 `pcSize`  
 [out] Wskaźnik na liczbę całkowitą, która określa rozmiar w bajtach, kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Aby zoptymalizować wydajność, środowiska uruchomieniowego w .NET Framework w wersji 2.0 dzieli wstępnie skompilowanych, natywny kod funkcji w wielu regionach. W związku z tym `GetCodeInfo` metoda jest przestarzała w programie .NET Framework 2.0, ponieważ jest nie może obsłużyć zakresu funkcji kodu macierzystego. Profilerzy powinni przełączyć się na użycie bardziej ogólnej `ICorProfilerInfo2::GetCodeInfo2` metody zamiast tego.  
  
 Ta funkcja używa bufory przypisane do obiektu wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
