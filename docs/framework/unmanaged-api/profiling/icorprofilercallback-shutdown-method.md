---
title: ICorProfilerCallback::Shutdown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb2bfe927eddaf6812b0185a586135e76f649c1b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728125"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown — Metoda
Powiadamia program profilujący, że aplikacja jest zamykana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Uwagi  
 Kod profilera nie można bezpiecznie wywołać metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu po `Shutdown` metoda jest wywoływana. Wszelkie wywołania `ICorProfilerInfo` metody spowodować niezdefiniowane zachowanie po `Shutdown` metoda zwraca. Niektóre zdarzenia niezmiennego nadal mogą wystąpić po zamknięciu systemu; Program profilujący powinien zajmie się do zwrócenia natychmiast w takiej sytuacji.  
  
 `Shutdown` Metoda zostanie wywołana tylko wtedy, gdy w aplikacji zarządzanej, która jest profilowana pracę jako kod zarządzany (czyli początkowej ramki na stosie proces odbywa się). Jeśli aplikacja uruchomiona jako kod niezarządzany, ale później wyniósł wywołanie kodu zarządzanego, tworząc wystąpienie środowisko uruchomieniowe języka wspólnego (CLR), następnie `Shutdown` nie zostaną wywołane. W takich przypadkach program profilujący powinien zawierać w swojej bibliotece `DllMain` procedura, która używa komunikat DLL_PROCESS_DETACH wartość zwolnić wszystkie zasoby do wykonywania oczyszczania przetwarzania swoich danych, takich jak opróżniania danych śledzenia na dysku, i tak dalej.  
  
 Ogólnie rzecz biorąc program profilujący musi sprostać nieoczekiwanego zamknięcia systemu. Na przykład proces może zostać wstrzymane przez firmy Win32 `TerminateProcess` — metoda (deklaracja w Winbase.h). W innych przypadkach CLR zostanie zatrzymany niektórych zarządzanych wątków (tła) bez dostarczanie wiadomości uporządkowany zniszczenie ich.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
