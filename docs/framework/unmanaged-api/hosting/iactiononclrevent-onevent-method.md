---
title: "IActionOnCLREvent::OnEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IActionOnCLREvent.OnEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b2f609969ccf67f07701d20578225f1618293968
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iactiononclreventonevent-method"></a>IActionOnCLREvent::OnEvent — Metoda
Wykonuje wywołania zwrotne na zdarzenia, które zostały zarejestrowane przy użyciu wywołania [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `event`  
 [in] Jeden z [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) wartości, które wskazuje typ zdarzenia.  
  
 `data`  
 [in] Wskaźnik do obiektu, który zawiera szczegółowe informacje o `event`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OnEvent`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do dowolnej metody hostingu zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `data` Parametr jest wskaźnik do obiektu nieokreślonego typu. Jeśli `event` parametr jest `Event_DomainUnload`, `data` jest identyfikator liczbowy <xref:System.AppDomain> który został zwolniony. Hosta można podjąć odpowiednie działania, przy użyciu tego identyfikatora jako klucza.  
  
 Jeśli `event` jest `Event_MDAFired`, `data` jest wskaźnikiem do [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) wystąpienia, które zawiera dane wyjściowe z zarządzanego debugowania Asystenta (MDA) komunikatu. Mda są funkcją środowiska CLR, która pomóc deweloperom z debugowaniem, generując XML komunikaty o zdarzeniach, które w przeciwnym razie są trudne do pułapki. Wysyłanie wiadomości tego może być szczególnie przydatne w debugowaniu przejścia między zarządzanymi i niezarządzanymi kodu. Aby uzyskać więcej informacji, zobacz [diagnozowanie problemów z Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [EClrEvent — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [IActionOnCLREvent — interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLROnEventManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [MDAInfo — struktura](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
