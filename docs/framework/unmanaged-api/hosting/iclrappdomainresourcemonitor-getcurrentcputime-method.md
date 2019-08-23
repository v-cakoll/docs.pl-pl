---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10245541718fd5e5f30ef6bba4ab289bcef767fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950206"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda
Pobiera łączny czas procesora, który był używany przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, od momentu utworzenia domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 podczas Identyfikator żądanej domeny aplikacji.  
  
 `pMilliseconds`  
 określoną Wskaźnik do łącznego czasu procesora, który był używany przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji od momentu utworzenia domeny aplikacji. Ten parametr może być `null`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|COR_E_APPDOMAINUNLOADED|Domena aplikacji została zwolniona lub nie istnieje.|  
|E_FAIL|Monitorowanie zasobów domeny aplikacji nie jest włączone.<br /><br /> —lub—<br /><br /> Wszystkie inne błędy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest niezarządzanym odpowiednikiem właściwości <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MetaHost.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAppDomainResourceMonitor, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Monitorowanie zasobów domen aplikacji](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
