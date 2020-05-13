---
title: ICorDebugManagedCallback2::MDANotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208528"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a>ICorDebugManagedCallback2::MDANotification — Metoda
Zapewnia powiadomienie, że wykonanie kodu napotkało asystenta zarządzanego debugowania (MDA) w debugowanej aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pController`  
 podczas Wskaźnik do interfejsu ICorDebugController, który uwidacznia proces lub domenę aplikacji, w której wystąpiło zdarzenie MDA.  
  
 Debuger nie powinien wprowadzać żadnych założeń dotyczących tego, czy kontroler jest procesem czy domeną aplikacji, chociaż zawsze może wysyłać zapytania do interfejsu w celu określenia.  
  
 `pThread`  
 podczas Wskaźnik do interfejsu ICorDebugThread, który uwidacznia zarządzany wątek, w którym wystąpiło zdarzenie debugowania.  
  
 Jeśli zdarzenie MDA wystąpił w niezarządzanym wątku, wartość `pThread` będzie równa null.  
  
 Musisz uzyskać identyfikator wątku systemu operacyjnego (OS) z samego obiektu MDA.  
  
 `pMDA`  
 podczas Wskaźnik do interfejsu [ICorDebugMDA](icordebugmda-interface.md) , który UWIDACZNIA informacje MDA.  
  
## <a name="remarks"></a>Uwagi  
 MDA jest ostrzeżeniem heurystycznym i nie wymaga żadnej jawnej akcji debugera z wyjątkiem wywołania [ICorDebugController:: Kontynuuj](icordebugcontroller-continue-method.md) , aby wznowić wykonywanie debugowanej aplikacji.  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) może określić, które MDA są wywoływane i które dane znajdują się w dowolnym punkcie. W związku z tym debugery nie powinny kompilować żadnej funkcjonalności wymagającej określonych wzorców MDA.  
  
 MDA może zostać umieszczona w kolejce i wyzwolona wkrótce po wystąpieniu MDA. Taka sytuacja może wystąpić, jeśli środowisko uruchomieniowe musi czekać, aż osiągnie bezpieczny punkt do uruchomienia MDA, zamiast wyzwalać zdarzenie MDA po jego napotkaniu. Oznacza to również, że środowisko uruchomieniowe może uruchamiać wiele MDA w jednym zestawie wywołań zwrotnych umieszczonych w kolejce (podobnie jak w przypadku operacji "Attach").  
  
 Debuger powinien zwolnić odwołanie do `ICorDebugMDA` wystąpienia natychmiast po powrocie z `MDANotification` wywołania zwrotnego, aby umożliwić środowisku CLR odtwarzanie pamięci używanej przez zdarzenie MDA. Zwolnienie wystąpienia może zwiększyć wydajność w przypadku uruchamiania wielu MDA.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [ICorDebugManagedCallback2 — Interfejs](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback — Interfejs](icordebugmanagedcallback-interface.md)
