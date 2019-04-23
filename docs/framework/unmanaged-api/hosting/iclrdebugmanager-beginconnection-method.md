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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b365aaa13b3070662a74ebcfc914f5ed3d291d76
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59133994"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection — Metoda
Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć listę zadań z identyfikatorem i przyjazną nazwę.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 [in] Identyfikator do skojarzenia z listą typowe zadania dotyczące języka wspólnego (CLR).  
  
 `szConnectionName`  
 [in] Przyjazną nazwę do skojarzenia z listy zadań CLR.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`BeginConnection` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|`dwConnectionId` wynosi zero, lub `BeginConnection` została już wywołana za pomocą tego `dwConnectionId` wartość lub `szConnectionName` ma wartość null.|  
|E_OUTOFMEMORY|Za mało pamięci może zostać przydzielone na potrzeby przechowywania na liście zadań skojarzonych z tym połączeniem.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrdebugmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) udostępnia trzy metody `BeginConnection`, [setconnectiontasks —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i [endconnection —](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md), kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.  
  
> [!IMPORTANT]
>  Te trzy metody musi zostać wywołany w określonej kolejności dla każdego zestawu zadań. `BeginConnection` nosi nazwę najpierw nawiązać nowe połączenie. `SetConnectionTasks` wywoływana jest następnie pozwalają na wybranie zestawu zadań, które mają być skojarzone z tego połączenia. `EndConnection` wywoływana jest ostatnia usunąć skojarzenie między listy zadań i identyfikator oraz przyjazną nazwę. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [EndConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
