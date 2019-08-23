---
title: ICLRErrorReportingManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966257"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager — Interfejs
Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów stosu na potrzeby raportowania błędów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginCustomDump, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Określa konfigurację niestandardowych zrzutów stosu dla raportowania błędów.|  
|[EndCustomDump, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Czyści konfigurację niestandardowego zrzutu stosu ustawioną w ramach wcześniejszego wywołania do `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.|  
  
## <a name="remarks"></a>Uwagi  
 `BeginCustomDump` Metoda ustawia konfigurację niestandardowego zrzutu stosu. `EndCustomDump` Metoda czyści konfigurację niestandardowego zrzutu stosu i zwalnia wszystkie powiązane Stany. Powinien być wywoływany po zakończeniu niestandardowego zrzutu.  
  
> [!IMPORTANT]
> Niepowodzenie wywołania `EndCustomDump` powoduje przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ECustomDumpItemKind, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
