---
title: IHostControl — Interfejs
ms.date: 03/30/2017
api_name:
- IHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl
helpviewer_keywords:
- IHostControl interface [.NET Framework hosting]
ms.assetid: a4ae0d1f-ade9-4b0a-a122-93ed11a5e6b3
topic_type:
- apiref
ms.openlocfilehash: 9dd89abb332853b966aa81dc506099b7af6ca3b2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804936"
---
# <a name="ihostcontrol-interface"></a>IHostControl — Interfejs
Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHostManager, metoda](ihostcontrol-gethostmanager-method.md)|Pobiera wskaźnik interfejsu do implementacji hosta interfejsu z określonym `IID` .|  
|[SetAppDomainManager, metoda](ihostcontrol-setappdomainmanager-method.md)|Powiadamia hosta o utworzeniu domeny aplikacji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.AppDomainManager>
- [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
