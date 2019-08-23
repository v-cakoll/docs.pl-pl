---
title: IGCHost2 — Interfejs
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21ce9cbd007858c0f39e12622eff819154ab83f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928614"
---
# <a name="igchost2-interface"></a>IGCHost2 — Interfejs
Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
> [!NOTE]
> W przypadku nowych rozwiązań zalecamy użycie interfejsu [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetGCStartupLimitsEx, metoda](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0. Włącza wartość generacji 0 i rozmiary segmentów `DWORD`większe niż.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** GCHost. idl, GCHost. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
