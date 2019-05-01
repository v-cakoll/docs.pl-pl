---
title: ICLRDomainManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce53149b92ca40ad50ecbefaf4701940e8567ae5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984753"
---
# <a name="iclrdomainmanager-interface"></a>ICLRDomainManager — Interfejs
Umożliwia hosta określić Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji i określić właściwości inicjowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetAppDomainManagerType, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setappdomainmanagertype-method.md)|Określa typ pochodną <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji.|  
|[SetPropertiesForDefaultAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|Ustawia właściwości, które będą używane do zainicjowania domyślnej domeny aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Aby pobrać wystąpienie tego interfejsu, należy wywołać [iclrcontrol::getclrmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody z typem Menedżera IID `IID_ICLRDomainManager`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
