---
title: "IHostPolicyManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostPolicyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostPolicyManager
helpviewer_keywords: IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0efbc0c51121156d112c63ba4ae59c6c9e95cd95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager — Interfejs
Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje środowisko uruchomieniowe języka wspólnego (CLR) w przypadku liczby przerywa przekroczenia limitu czasu lub błędów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnDefaultAction, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Powiadamia hosta, który ma mieć domyślne działanie określony przez wywołanie do środowiska CLR [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na wątek przerwania lub <xref:System.AppDomain> zwolnienia.|  
|[OnFailure, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.|  
|[OnTimeout, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na przekroczenie limitu czasu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EClrOperation, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)  
 [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
