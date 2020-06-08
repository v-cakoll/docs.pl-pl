---
title: ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0a4cb365ca8f7d52be505368a3d769a9728983bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502967"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda
Pobiera obiekt, który może być badany dla interfejsu ICorDebugThread. Ta metoda jest przestarzała w .NET Framework w wersji 2,0.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppicd`  
 Obiekt [out](/cpp/atl/iunknown) , który może być badany dla `ICorDebugThread` interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Usługi debugowania środowiska uruchomieniowego języka wspólnego (CLR) obsługują ograniczone debugowanie w procesie w .NET Framework w wersji 1,0. Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania. W wyniku opinii klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersja .NET Framework:** 1,0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
