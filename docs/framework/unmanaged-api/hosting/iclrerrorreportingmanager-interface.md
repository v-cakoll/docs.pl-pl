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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616999"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager — Interfejs
Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów stosu na potrzeby raportowania błędów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginCustomDump, metoda](iclrerrorreportingmanager-begincustomdump-method.md)|Określa konfigurację niestandardowych zrzutów stosu dla raportowania błędów.|  
|[EndCustomDump, metoda](iclrerrorreportingmanager-endcustomdump-method.md)|Czyści konfigurację niestandardowego zrzutu stosu ustawioną w ramach wcześniejszego wywołania do `BeginCustomDump` .|  
|[GetBucketParametersForCurrentException, metoda](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Pobiera pakiet programu Watson dla bieżącego wyjątku w wątku wywołującym.|  
  
## <a name="remarks"></a>Uwagi  
 `BeginCustomDump`Metoda ustawia konfigurację niestandardowego zrzutu stosu. `EndCustomDump`Metoda czyści konfigurację niestandardowego zrzutu stosu i zwalnia wszystkie powiązane Stany. Powinien być wywoływany po zakończeniu niestandardowego zrzutu.  
  
> [!IMPORTANT]
> Niepowodzenie wywołania `EndCustomDump` powoduje przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ECustomDumpItemKind, wyliczenie](ecustomdumpitemkind-enumeration.md)
- [Hosting, interfejsy](hosting-interfaces.md)
