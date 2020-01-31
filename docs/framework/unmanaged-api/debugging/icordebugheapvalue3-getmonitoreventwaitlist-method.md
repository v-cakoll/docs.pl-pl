---
title: ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 15900fab59d172ada67d8aefeab698e1b44f808e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794392"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda
Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce dla zdarzenia, które jest skojarzone z blokadą monitora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 określoną Moduł wyliczający ICorDebugThreadEnum, który dostarcza uporządkowaną listę wątków.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Lista nie jest pusta.|  
|S_FALSE|Lista jest pusta.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy wątek na liście to pierwszy wątek, który jest wydawany przez następne wywołanie do <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Następny wątek na liście jest publikowany w następującym wywołaniu i tak dalej.  
  
 Jeśli lista nie jest pusta, metoda zwraca S_OK. Jeśli lista jest pusta, metoda zwraca S_FALSE; w takim przypadku Wyliczenie jest nadal ważne, chociaż jest puste.  
  
 W obu przypadkach interfejs wyliczenia jest używany tylko na czas trwania bieżącego zsynchronizowanego stanu. Jednak interfejsy wątku są od niego ważne do momentu zakończenia wątku.  
  
 Jeśli `ppThreadEnum` nie jest prawidłowym wskaźnikiem, wynik jest niezdefiniowany.  
  
 Jeśli wystąpi błąd, aby nie można było ustalić, który, jeśli istnieje, wątki oczekują na monitor, metoda zwraca wartość HRESULT, która wskazuje na błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
