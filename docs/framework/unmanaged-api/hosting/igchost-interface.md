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
ms.openlocfilehash: 91483d5bdf1eb8e6b03d7691e2a95074e3789317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134883"
---
# <a name="igchost-interface"></a>IGCHost — Interfejs
Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
> [!NOTE]
> Począwszy od .NET Framework 4,5, można użyć metody [IGCHost2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu odzyskiwania pamięci na wartość większą niż limit `DWORD` nałożona przez metodę [SetGCStartupLimits —](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) .  
  
> [!NOTE]
> Ten interfejs jest przeznaczony tylko dla ekspertów. Może mieć wpływ na wydajność aplikacji, jeśli jest używana nieprawidłowo.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|Wymusza, aby kolekcja była wykonywana dla danej generacji, niezależnie od stanu bieżącej wyrzucania elementów bezużytecznych.|  
|[GetStats, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.|  
|[GetThreadStats, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.|  
|[SetGCStartupLimits, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.|  
|[SetVirtualMemLimit, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
