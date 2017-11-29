---
title: "ICLRGCManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager
helpviewer_keywords: ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7215ce1423e8541b23daae7b9e051ade6e25f1b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager — Interfejs
Udostępnia metody umożliwiające hosta do interakcji z systemem zbierania odzyskiwanie środowisko uruchomieniowe języka wspólnego firmy.  
  
> [!NOTE]
>  Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można użyć [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, aby wartość rozmiaru segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0 wartości większą niż `DWORD` limit, który jest narzucone przez [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.|  
|[GetStats — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|Pobiera zestaw bieżącego Statystyka systemu czyszczenia pamięci.|  
|[SetGCStartupLimits — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm kolekcji jego odzyskiwanie z zarządzanego <xref:System.GC> typu. Aby uzyskać więcej informacji o systemie kolekcji pamięci, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Automatyczne zarządzanie pamięcią](../../../../docs/standard/automatic-memory-management.md)  
 [Cor_gc_stats — struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
