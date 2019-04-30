---
title: IHostPolicyManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9d903b4e44ea7a185ad8b3b71b7a5da2f2bda3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760119"
---
# <a name="ihostpolicymanager-interface"></a>IHostPolicyManager — Interfejs
Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje środowisko uruchomieniowe języka wspólnego (CLR) w przypadku właściwości przerywa przekroczenia limitu czasu lub niepowodzenia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnDefaultAction, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|Powiadamia hosta, który ma mieć domyślne działanie określony przez wywołanie do środowiska CLR [iclrpolicymanager::setdefaultaction —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) w odpowiedzi na wątek przerwania lub <xref:System.AppDomain> zwolnienia.|  
|[OnFailure, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [iclrpolicymanager::setactiononfailure —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) w odpowiedzi na błąd alokacji lub odzyskiwanie zasobu.|  
|[OnTimeout, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|Powiadamia hosta, który ma mieć z akcją określoną przez wywołanie do środowiska CLR [iclrpolicymanager::setactionontimeout —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) w odpowiedzi na przekroczenie limitu czasu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EClrFailure, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EClrOperation, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
