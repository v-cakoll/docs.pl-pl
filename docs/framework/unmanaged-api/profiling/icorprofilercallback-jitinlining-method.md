---
title: ICorProfilerCallback::JITInlining — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782803"
---
# <a name="icorprofilercallbackjitinlining-method"></a>ICorProfilerCallback::JITInlining — Metoda
Powiadamia program profilujący, że kompilator just-in-time (JIT) zostanie Wstawianie funkcji z innej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a>Parametry  
 `callerId`  
 [in] Identyfikator funkcji, do którego `calleeId` zostanie wstawiona funkcja.  
  
 `calleeId`  
 [in] Identyfikator funkcji ma zostać wstawiony.  
  
 `pfShouldInline`  
 [out] `true` do wstawiania występuje; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący może ustawić `pfShouldInline` do `false` zapobiegające `calleeId` funkcji z jest wstawiany do `callerId` funkcji. Ponadto program profilujący globalnie wyłączyć wstawiania wbudowane za pomocą wartość COR_PRF_DISABLE_INLINING [cor_prf_monitor —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) wyliczenia.  
  
 Wbudowane funkcje wstawione nieznakowe inicjują zdarzenia o. W związku z tym, należy ustawić program profilujący `pfShouldInline` do `false` aby wygenerować dokładne Wykres wywołań. Ustawienie `pfShouldInline` do `false` będzie mieć wpływ na wydajność, ponieważ wstawiania wbudowane zwykle zwiększa szybkość i zmniejsza liczbę oddzielnych zdarzenia kompilacji JIT dla wstawionych metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
