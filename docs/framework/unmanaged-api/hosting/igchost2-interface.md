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
ms.openlocfilehash: 976673a0caab4e041cc80e5536544c195fcf692a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805179"
---
# <a name="igchost2-interface"></a>IGCHost2 — Interfejs
Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
> [!NOTE]
> W przypadku nowych rozwiązań zalecamy użycie interfejsu [ICLRGCManager2](iclrgcmanager2-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetGCStartupLimitsEx, metoda](igchost2-setgcstartuplimitsex-method.md)|Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0. Włącza wartość generacji 0 i rozmiary segmentów większe niż `DWORD` .|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost. idl, GCHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
- [Interfejsy hostingu środowiska CLR](clr-hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](corruntimehost-coclass.md)
