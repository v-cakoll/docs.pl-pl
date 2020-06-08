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
ms.openlocfilehash: f878e2f1f86bc42c0ff5abada8d7df4feb9ed228
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504200"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager — Interfejs
Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.  
  
> [!NOTE]
> Począwszy od .NET Framework 4,5, można użyć metody [ICLRGCManager2:: SetGCStartupLimitsEx —](iclrgcmanager2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu wyrzucania elementów bezużytecznych z wartości większej niż `DWORD` Limit narzucony przez metodę [SetGCStartupLimits —](iclrgcmanager-setgcstartuplimits-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Collect, metoda](iclrgcmanager-collect-method.md)|Wymusza wyrzucanie elementów bezużytecznych dla określonej generacji.|  
|[GetStats, metoda](iclrgcmanager-getstats-method.md)|Pobiera zestaw bieżących statystyk dotyczących systemu odzyskiwania pamięci.|  
|[SetGCStartupLimits, metoda](iclrgcmanager-setgcstartuplimits-method.md)|Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm wyrzucania elementów bezużytecznych z typem zarządzanym <xref:System.GC> . Aby uzyskać więcej informacji na temat systemu wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Automatyczne zarządzanie pamięcią](../../../standard/automatic-memory-management.md)
- [COR_GC_STATS, struktura](cor-gc-stats-structure.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [Interfejsy hostingu środowiska CLR](clr-hosting-interfaces.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
