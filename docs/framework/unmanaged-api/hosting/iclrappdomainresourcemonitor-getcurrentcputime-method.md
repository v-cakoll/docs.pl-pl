---
title: "ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2483165de54cd5ec76abad9d8472e0deef28f149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime — Metoda
Pobiera całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, ponieważ domena aplikacji została utworzona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [in] Identyfikator domeny żądanej aplikacji.  
  
 `pMilliseconds`  
 [out] Wskaźnik do całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, ponieważ domena aplikacji została utworzona. Ten parametr może być `null`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|COR_E_APPDOMAINUNLOADED|Domeny aplikacji został zwolniony lub nie istnieje.|  
|E_FAIL|Nie włączono monitorowania zasobów domen aplikacji.<br /><br /> —lub—<br /><br /> Wszystkie inne błędy.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest odpowiednikiem niezarządzane zarządzanej <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> właściwości.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAppDomainResourceMonitor — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Zasobów domen aplikacji monitorowania](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
