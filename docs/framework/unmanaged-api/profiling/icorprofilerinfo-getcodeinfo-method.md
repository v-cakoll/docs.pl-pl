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
ms.openlocfilehash: 21dc937bef2bbe197a5dc4af72ff50dff64dbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454146"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo — Metoda
Pobiera zakres skojarzony z identyfikatorem. określona funkcja kodu natywnego  
  
 Ta metoda jest przestarzała. Użyj [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [in] Identyfikator funkcji, z którym jest skojarzona kodu natywnego.  
  
 `pStart`  
 [out] Wskaźnik do tablicy bajtów, które tworzą kodu natywnego funkcji.  
  
 `pcSize`  
 [out] Wskaźnik do liczba całkowita określająca rozmiar w bajtach kodu natywnego.  
  
## <a name="remarks"></a>Uwagi  
 Aby zoptymalizować wydajność, środowiska uruchomieniowego w programie .NET Framework w wersji 2.0 dzieli prekompilowany natywnego kodu funkcji na wielu regionach. W rezultacie `GetCodeInfo` metoda jest przestarzałe w programie .NET Framework 2.0, ponieważ nie jest w stanie obsłużyć w zakresie funkcji kodu natywnego. Profilery powinien rozpocząć korzystanie z bardziej ogólnym `ICorProfilerInfo2::GetCodeInfo2` metody zamiast tego.  
  
 Ta funkcja korzysta buforów przydzielone przez obiekt wywołujący.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
