---
title: IActionOnCLREvent::OnEvent — Metoda
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e7045d3b095b6a35be8b55e1066b459e9583c93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147020"
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent — Metoda
Wykonuje wywołania zwrotne dla zdarzenia, które zostały zarejestrowane przy użyciu wywołania [iclroneventmanager::registeractiononevent —](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `event`  
 [in] Jedną z [eclrevent —](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, które wskazuje typ zdarzenia.  
  
 `data`  
 [in] Wskaźnik do obiektu, który zawiera szczegółowe informacje o `event`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OnEvent` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do dowolnej metody hostowania zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `data` Parametr jest wskaźnikiem do obiektu nieokreślonego typu. Jeśli `event` parametr jest `Event_DomainUnload`, `data` jest identyfikator liczbowy <xref:System.AppDomain> , został usunięty z pamięci. Hosta można podjąć odpowiednie działania, o których jako klucz przy użyciu tego identyfikatora.  
  
 Jeśli `event` jest `Event_MDAFired`, `data` jest wskaźnikiem do [mdainfo —](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera dane wyjściowe komunikatu z zarządzanego debugowania Asystenta ustawień (MDA). Mda są funkcją środowiska CLR, które pomogą w debugowaniu, generując XML komunikaty o zdarzeniach, które w przeciwnym razie są trudne do pułapki. Takie wiadomości może być szczególnie przydatne podczas debugowania przejścia między kodem zarządzanym i niezarządzanym. Aby uzyskać więcej informacji, zobacz [diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [EClrEvent, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLROnEventManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [MDAInfo, struktura](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
