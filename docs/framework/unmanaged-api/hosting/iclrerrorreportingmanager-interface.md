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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129254"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager — Interfejs
Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów stosu na potrzeby raportowania błędów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginCustomDump, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Określa konfigurację niestandardowych zrzutów stosu dla raportowania błędów.|  
|[EndCustomDump, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Czyści konfigurację niestandardowego zrzutu stosu ustawioną przez wcześniejsze wywołanie do `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `BeginCustomDump` ustawia konfigurację niestandardowego zrzutu stosu. Metoda `EndCustomDump` czyści konfigurację niestandardowego zrzutu stosu i zwalnia wszystkie powiązane Stany. Powinien być wywoływany po zakończeniu niestandardowego zrzutu.  
  
> [!IMPORTANT]
> Nie można wywołać `EndCustomDump` powoduje przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ECustomDumpItemKind, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
