---
title: "ICorProfilerCallback::Shutdown — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Shutdown
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c9abc3c255f7ddda5e7934c495b073a7b1f6fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown — Metoda
Powiadamia profilera, że aplikacja jest zamykana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod profilera bezpiecznie nie można wywołać metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu po `Shutdown` metoda jest wywoływana. Wszelkie wywołania `ICorProfilerInfo` metod spowodować niezdefiniowane zachowanie po `Shutdown` zwraca metody. Określone zdarzenia niezmienne nadal może wystąpić po zamknięciu; profilera należy zwrócić uwagę, aby zwrócić natychmiast w takiej sytuacji.  
  
 `Shutdown` Metoda zostanie wywołana tylko wtedy, gdy aplikacja zarządzana, który jest poddawany profilowaniu uruchomiona jako kodu zarządzanego (to znaczy początkowej ramek na stosie proces odbywa się). Jeśli aplikacja uruchomiona jako kodu niezarządzanego, ale później przeskoki do kodu zarządzanego, tworząc wystąpienia środowisko uruchomieniowe języka wspólnego (CLR), następnie `Shutdown` nie zostanie wywołana. W tych przypadkach profilera, należy uwzględnić w jego biblioteki `DllMain` procedury, która używa komunikat DLL_PROCESS_DETACH wartość, aby zwolnić wszystkie zasoby i przetwarzania oczyszczania jej dane, takie jak opróżnianie ślady na dysku i tak dalej.  
  
 Ogólnie rzecz biorąc profilera musi sprostać zamknięć. Na przykład proces może być zatrzymana przez Win32 w `TerminateProcess` — metoda (deklaracja w Winbase.h). W innych przypadkach CLR spowoduje zatrzymanie niektórych zarządzanych wątków (tła) bez dostarczanie wiadomości uporządkowany zniszczenie dla nich.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Initialize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
