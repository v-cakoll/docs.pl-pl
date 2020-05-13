---
title: ICorDebugThread::SetDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: 05ae2791ee7f8bd31be38ec4d2117ddc3c2ea2bc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377942"
---
# <a name="icordebugthreadsetdebugstate-method"></a>ICorDebugThread::SetDebugState — Metoda
Ustawia flagi opisujące stan debugowania tego ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 podczas Bitowa kombinacja CorDebugThreadState — wartości wyliczenia, które określają stan debugowania tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 `SetDebugState`ustawia bieżący stan debugowania wątku. ("Bieżący stan debugowania" reprezentuje stan debugowania, jeśli proces ma być kontynuowany, a nie z rzeczywistym bieżącym stanem). Wartość normalna jest THREAD_RUN. Tylko debuger może mieć wpływ na stan debugowania wątku. Stany debugowania są w dalszym ciągu kontynuowane, więc jeśli chcesz utrzymywać wątek THREAD_SUSPENDed przez wiele kontynuuje, możesz go skonfigurować raz i jeszcze nie musi się martwić. Wstrzymywanie wątków i wznawianie procesu może spowodować zakleszczenie, chociaż zwykle jest to mało prawdopodobne. Jest to wewnętrzna jakość wątków i procesów. jest ona zaprojektowana. Debuger może asynchronicznie przerwać i wznowić wątki w celu przerwania zakleszczenia. Jeśli stan użytkownika wątku zawiera USER_UNSAFE_POINT, wątek może blokować wyrzucanie elementów bezużytecznych (GC). Oznacza to, że zawieszony wątek ma znacznie większą szansę na spowodowanie zakleszczenia. To może nie wpływać na zdarzenia debugowania, które zostały już dodane do kolejki. W ten sposób debuger powinien opróżnić całą kolejkę zdarzeń (przez wywołanie [ICorDebugController:: HasQueuedCallbacks —](icordebugcontroller-hasqueuedcallbacks-method.md)) przed zawieszeniem lub wznowieniem wątków. W przeciwnym razie mogą wystąpić zdarzenia w wątku, który uważa, że jest już wstrzymany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
