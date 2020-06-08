---
title: ICLRDebugManager::BeginConnection — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 98e4efe149cab1b822c9993e4df28806f773c61d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504254"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection — Metoda
Ustanawia nowe połączenie między hostem i debugerem w celu skojarzenia listy zadań z identyfikatorem i przyjazną nazwą.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 podczas Identyfikator do skojarzenia z listą zadań środowiska uruchomieniowego języka wspólnego (CLR).  
  
 `szConnectionName`  
 podczas Przyjazna nazwa do skojarzenia z listą zadań CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`BeginConnection`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|`dwConnectionId`zero lub `BeginConnection` zostało już wywołane przy użyciu tej `dwConnectionId` wartości lub `szConnectionName` miało wartość null.|  
|E_OUTOFMEMORY|Za mało pamięci, aby pomieścić listę zadań skojarzonych z tym połączeniem.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRDebugManager](iclrdebugmanager-interface.md) udostępnia trzy metody, `BeginConnection` , [SetConnectionTasks —](iclrdebugmanager-setconnectiontasks-method.md)i [EndConnection —](iclrdebugmanager-endconnection-method.md), do kojarzenia list zadań z identyfikatorami i przyjaznymi nazwami.  
  
> [!IMPORTANT]
> Te trzy metody muszą być wywoływane w określonej kolejności dla każdego zestawu zadań. `BeginConnection`jest wywoływana najpierw w celu nawiązania nowego połączenia. `SetConnectionTasks`jest wywoływana dalej, aby określić zestaw zadań, które mają być skojarzone z tym połączeniem. `EndConnection`jest wywoływana jako Ostatnia, aby usunąć skojarzenie między listą zadań a identyfikatorem i przyjazną nazwą. Jednak wywołania dla różnych połączeń mogą być zagnieżdżane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLRDebugManager, interfejs](iclrdebugmanager-interface.md)
- [EndConnection, metoda](iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks, metoda](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl, interfejs](ihostcontrol-interface.md)
