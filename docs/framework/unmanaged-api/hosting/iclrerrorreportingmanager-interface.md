---
title: "ICLRErrorReportingManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590cd87d6a566e9c8c3819fd1b250997938e9c35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager — Interfejs
Udostępnia metody umożliwiające hosta skonfigurować zrzuty stosu niestandardowych dla usługi raportowania błędów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginCustomDump — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.|  
|[EndCustomDump — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Czyści konfiguracji zrzutu niestandardowych stos został ustawiony przez wywołanie wcześniejszych `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Pobiera bieżący wyjątek w wątku wywołującym pakiet programu Watson.|  
  
## <a name="remarks"></a>Uwagi  
 `BeginCustomDump` Metoda ustawia Konfiguracja zrzutu stosu niestandardowych. `EndCustomDump` Metody spowoduje wyczyszczenie stosu niestandardowej konfiguracji zrzutu i zwalnia każdy stan skojarzony. Należy wywołać po wykonaniu zrzutu niestandardowych.  
  
> [!IMPORTANT]
>  Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ECustomDumpItemKind — wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
