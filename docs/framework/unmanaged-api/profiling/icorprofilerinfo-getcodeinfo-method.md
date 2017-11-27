---
title: "ICorProfilerInfo::GetCodeInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCodeInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0b5c7b0d932200f04df0a1a84dd1f747b7945943
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
