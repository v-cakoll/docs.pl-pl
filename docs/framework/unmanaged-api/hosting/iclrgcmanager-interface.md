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
ms.openlocfilehash: 045b924033630ea98d5a532a62f1037a5972df90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433927"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager — Interfejs
Udostępnia metody umożliwiające hosta do interakcji z systemem zbierania odzyskiwanie środowisko uruchomieniowe języka wspólnego firmy.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można użyć [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, aby wartość rozmiaru segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0 wartości większą niż `DWORD` limit, który jest narzucone przez [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.|  
|[GetStats, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Pobiera zestaw bieżącego Statystyka systemu czyszczenia pamięci.|  
|[SetGCStartupLimits, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm kolekcji jego odzyskiwanie z zarządzanego <xref:System.GC> typu. Aby uzyskać więcej informacji o systemie kolekcji pamięci, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyczne zarządzanie pamięcią](../../../../docs/standard/automatic-memory-management.md)  
 [COR_GC_STATS, struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
