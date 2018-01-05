---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList — Metoda
Udostępnia uporządkowaną listę wątków oczekujących w kolejce na zdarzenie, które jest skojarzone z blokadą monitora.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppThreadEnum`  
 [out] Moduł wyliczający ICorDebugThreadEnum, który zawiera listy uporządkowanej wątków.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Lista nie jest pusta.|  
|WARTOŚCI S_FALSE|Lista jest pusta.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Pierwszym wątkiem w liście jest pierwszym wątkiem wydane przez następne wywołanie <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Następny wątek na liście jest wydany następujące wywołanie i tak dalej.  
  
 Jeśli lista nie jest pusty, ta metoda zwraca wartość S_OK. Jeśli lista jest pusta, metoda zwraca wartości S_FALSE; w takim przypadku wyliczenie jest nadal ważny, chociaż nie jest pusty.  
  
 W obu przypadkach interfejs wyliczenie jest możliwe tylko na czas trwania bieżącego stanu zsynchronizowane. Jednak zrezygnować z niej interfejsy wątku są prawidłowe, dopóki kończy działanie wątku.  
  
 Jeśli `ppThreadEnum` nie jest wskaźnikiem prawidłowe, wynikiem jest niezdefiniowany.  
  
 W przypadku wystąpienia błędu w taki sposób, że nie można ustalić, które, wątków oczekujących monitora, metoda zwraca HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
