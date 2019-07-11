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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db34d56fd4d074551ca4823681bc5d94e76df758
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756618"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda
Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce na zdarzenia skojarzonego z blokadą monitora.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 [out] Icordebugthreadenum — moduł wyliczający, który zawiera uporządkowaną listę wątków.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Lista nie jest pusta.|  
|S_FALSE|Lista jest pusta.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Pierwszym wątku na liście jest pierwszym wątkiem, który jest wydane przez następne wywołanie <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Następny wątek na liście jest wydawane w następujące wywołanie i tak dalej.  
  
 Jeśli lista nie jest pusty, ta metoda zwraca wartość S_OK. Jeśli lista jest pusta, metoda zwraca wartość S_FALSE; w tym przypadku wyliczenia jest nadal ważny, mimo że jest on pusty.  
  
 W obu przypadkach interfejs wyliczenia jest można używać tylko na czas trwania bieżącego stanu zsynchronizowane. Jednak interfejsów wątku zrezygnować z niego są prawidłowe, aż wątek kończy działanie.  
  
 Jeśli `ppThreadEnum` nie jest prawidłową wskaźnikiem, wynik jest niezdefiniowany.  
  
 W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, który, wątki oczekują na monitorze, metoda zwraca wartość HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
