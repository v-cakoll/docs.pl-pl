---
title: ICLROnEventManager::RegisterActionOnEvent — Metoda
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
ms.openlocfilehash: e634b3876d51d461446ed3f5ae537ac1db1545bd
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703503"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a>ICLROnEventManager::RegisterActionOnEvent — Metoda
Rejestruje wskaźnik wywołania zwrotnego dla określonego zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `event`  
 podczas Jedna z wartości [EClrEvent —](eclrevent-enumeration.md) , wskazująca na zdarzenie, dla którego ma zostać zarejestrowany wskaźnik wywołania zwrotnego opisany przez `pAction` .  
  
 `pAction`  
 podczas Wskaźnik do obiektu [IActionOnCLREvent](iactiononclrevent-interface.md) , który jest wywoływany po uruchomieniu zarejestrowanego zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`RegisterActionOnEvent`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Host może rejestrować wywołania zwrotne dla jednego lub obu typów zdarzeń opisanych przez `EClrEvent` . Host pobiera `ICLROnEventManager` interfejs, wywołując metodę [ICLRControl:: GetCLRManager —](iclrcontrol-getclrmanager-method.md) .  
  
> [!NOTE]
> Zdarzenia, które `RegisterActionOnEvent` rejestry mogą być wywoływane więcej niż jeden raz i z różnych wątków, aby sygnalizować zwolnienie lub wyłączenie środowiska CLR.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrEvent, wyliczenie](eclrevent-enumeration.md)
- [IActionOnCLREvent — Interfejs](iactiononclrevent-interface.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICLROnEventManager, interfejs](iclroneventmanager-interface.md)
