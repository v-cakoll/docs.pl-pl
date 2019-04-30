---
title: ICLRGCManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9519f7c2df5cf078bac6be038275527d7741edb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700842"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager — Interfejs
Udostępnia metody, które umożliwiają hosta do interakcji z systemem kolekcji wyrzucania elementów wykonywalnych języka wspólnego.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], możesz użyć [iclrgcmanager2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, aby ustawić rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 do wartości większej niż `DWORD` limit, który jest narzucone przez [setgcstartuplimits —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.|  
|[GetStats, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Pobiera zestaw statystyk bieżące informacje o systemie kolekcji wyrzucania elementów.|  
|[SetGCStartupLimits, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) implementuje jego mechanizm kolekcji wyrzucania elementów z zarządzaną <xref:System.GC> typu. Aby uzyskać więcej informacji na temat systemu czyszczenia pamięci zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Automatyczne zarządzanie pamięcią](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS, struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
