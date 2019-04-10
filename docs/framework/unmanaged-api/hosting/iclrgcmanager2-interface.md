---
title: ICLRGCManager2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a89a7ef34418163d790fd055de681c1cdf989e57
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226927"
---
# <a name="iclrgcmanager2-interface"></a>ICLRGCManager2 — Interfejs
Udostępnia metody, które umożliwiają hosta do interakcji z systemem kolekcji wyrzucania elementów wykonywalnych języka wspólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetGCStartupLimitsEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0. Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs dziedziczy [iclrgcmanager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).  
  
 Środowisko uruchomieniowe języka wspólnego (CLR) implementuje jego mechanizm kolekcji wyrzucania elementów z zarządzaną <xref:System.GC> typu. Aby uzyskać więcej informacji na temat systemu czyszczenia pamięci zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Automatyczne zarządzanie pamięcią](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS — Struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
