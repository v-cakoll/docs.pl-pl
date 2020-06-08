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
ms.openlocfilehash: eb6efc738b270f8f76d7130a12af4927fb6220ce
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498365"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo — Metoda
Pobiera zakres kodu natywnego skojarzonego z określonym IDENTYFIKATORem funkcji.  
  
 Ta metoda jest przestarzała. Zamiast tego użyj metody [ICorProfilerInfo2:: GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.  
  
 `pStart`  
 określoną Wskaźnik do tablicy bajtów składających się na kod natywny funkcji.  
  
 `pcSize`  
 określoną Wskaźnik do liczby całkowitej, która określa rozmiar (w bajtach) kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Aby zoptymalizować wydajność, środowisko uruchomieniowe w .NET Framework w wersji 2,0 dzieli wstępnie skompilowany kod natywny funkcji na wiele regionów. W związku z tym `GetCodeInfo` Metoda jest przestarzała w .NET Framework 2,0, ponieważ nie jest w stanie obsłużyć zakresu kodu natywnego funkcji. W zamian należy przełączyć się na używanie bardziej ogólnej `ICorProfilerInfo2::GetCodeInfo2` metody.  
  
 Ta funkcja używa buforów przyznanych przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
