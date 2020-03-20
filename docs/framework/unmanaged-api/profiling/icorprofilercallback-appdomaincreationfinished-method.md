---
title: ICorProfilerCallback::AppDomainCreationFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177075"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a>ICorProfilerCallback::AppDomainCreationFinished — Metoda
Powiadamia profiler, że domena aplikacji została utworzona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a>Parametry

- `appDomainId`

  \[w] Identyfikuje domenę, która została utworzona.

- `hrStatus`

  \[w] HRESULT, który wskazuje, czy tworzenie domeny aplikacji zostało pomyślnie zakończone.

## <a name="remarks"></a>Uwagi  
 Identyfikator aplikacji nie jest prawidłowy dla `AppDomainCreationFinished` każdego żądania informacji, dopóki metoda nie zostanie wywołana.  
  
 Niektóre części ładowania domeny aplikacji może `AppDomainCreationFinished` być kontynuowana po wywołaniu zwrotnym. Błąd HRESULT `hrStatus` w wskazuje na błąd. Jednak sukces HRESULT `hrStatus` w wskazuje tylko, że pierwsza część tworzenia domeny aplikacji powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorProfilerCallback — Interfejs](icorprofilercallback-interface.md)
