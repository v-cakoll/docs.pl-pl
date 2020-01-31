---
title: ICorProfilerInfo::EndInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 8a15843e9169442d89996375ee85f62b38f92e30
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864261"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging — Metoda
Zamyka sesję debugowania w procesie. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwProfilerContext`  
 podczas Wartość, która identyfikuje sesję debugowania. Ta wartość musi być taka sama jak odebrana w metodzie [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.  
  
 Usługi debugowania CLR obsługiwały ograniczone debugowanie w procesie w .NET Framework wersje 1,0 i 1,1. Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania. Jednak ze względu na Opinie klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersja .NET Framework:** 1,0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
