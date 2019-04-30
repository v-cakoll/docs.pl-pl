---
title: IGCHost — Interfejs
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3202aa25261863dae953e3edac36f3406fa001d8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699766"
---
# <a name="igchost-interface"></a>IGCHost — Interfejs
Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], możesz użyć [igchost2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, aby ustawić rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 wartości większe niż `DWORD` limit, który jest narzucone przez [setgcstartuplimits —](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metody.  
  
> [!NOTE]
>  Ten interfejs jest wyłącznie na potrzeby ekspertów. To wpłynąć na wydajność aplikacji użycie nieprawidłowo.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Wymusza kolekcji wystąpi dla danej generacji, bez względu na stan bieżącej operacji wyrzucania elementów bezużytecznych.|  
|[GetStats, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.|  
|[GetThreadStats, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Pobiera statystyki wątku wyrzucania elementów bezużytecznych.|  
|[SetGCStartupLimits, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.|  
|[SetVirtualMemLimit, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Ustawia maksymalny rozmiar pamięci wirtualnej w środowisku uruchomieniowym.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl, GCHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
