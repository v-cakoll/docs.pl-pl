---
title: ICorProfilerCallback::AppDomainShutdownFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
ms.openlocfilehash: 0851ac33a2bac4fcf727cf09e5225f6b83481b50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866679"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished — Metoda
Powiadamia profiler o tym, że domena aplikacji została zwolniona z procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry

- `appDomainId`

  \[in] określa domenę, w której są przechowywane zestawy aplikacji.

- `hrStatus`

  \[in] wynik HRESULT wskazujący, czy domena aplikacji została zwolniona pomyślnie.

## <a name="remarks"></a>Uwagi  
 Wartość `appDomainId` nie jest prawidłowa dla żądania informacji po powrocie metody [ICorProfilerCallback:: AppDomainShutdownStarted —](icorprofilercallback-appdomainshutdownstarted-method.md) .  
  
 Niektóre części zwalniania domeny aplikacji mogą być kontynuowane po wywołaniu wywołania zwrotnego `AppDomainCreationFinished`. Błąd HRESULT w `hrStatus` wskazuje na błąd. Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania domeny aplikacji zakończyła się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
