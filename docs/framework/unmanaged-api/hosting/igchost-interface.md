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
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805217"
---
# <a name="igchost-interface"></a>IGCHost — Interfejs
Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
> [!NOTE]
> Począwszy od .NET Framework 4,5, można użyć metody [IGCHost2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu wyrzucania elementów bezużytecznych z wartości większej niż `DWORD` Limit narzucony przez metodę [SetGCStartupLimits —](igchost-setgcstartuplimits-method.md) .  
  
> [!NOTE]
> Ten interfejs jest przeznaczony tylko dla ekspertów. Może mieć wpływ na wydajność aplikacji, jeśli jest używana nieprawidłowo.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](igchost-collect-method.md)|Wymusza, aby kolekcja była wykonywana dla danej generacji, niezależnie od stanu bieżącej wyrzucania elementów bezużytecznych.|  
|[GetStats, metoda](igchost-getstats-method.md)|Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.|  
|[GetThreadStats, metoda](igchost-getthreadstats-method.md)|Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.|  
|[SetGCStartupLimits, metoda](igchost-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.|  
|[SetVirtualMemLimit, metoda](igchost-setvirtualmemlimit-method.md)|Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](corruntimehost-coclass.md)
