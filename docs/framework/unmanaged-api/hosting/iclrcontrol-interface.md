---
title: ICLRControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615842"
---
# <a name="iclrcontrol-interface"></a>ICLRControl — Interfejs
Dostarcza metody, które umożliwiają hostowi uzyskanie odwołań do i Konfigurowanie aspektów środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCLRManager, metoda](iclrcontrol-getclrmanager-method.md)|Pobiera wskaźnik interfejsu do wystąpienia dowolnego typu Menedżera, którego host może użyć do skonfigurowania środowiska CLR.|  
|[SetAppDomainManagerType, metoda](iclrcontrol-setappdomainmanagertype-method.md)|Ustawia typ pochodzący od <xref:System.AppDomainManager> typu dla menedżerów domeny aplikacji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager, interfejs](iclrassemblyidentitymanager-interface.md)
- [ICLRDebugManager, interfejs](iclrdebugmanager-interface.md)
- [ICLRGCManager, interfejs](iclrgcmanager-interface.md)
- [ICLRHostBindingPolicyManager, interfejs](iclrhostbindingpolicymanager-interface.md)
- [ICLRHostProtectionManager, interfejs](iclrhostprotectionmanager-interface.md)
- [ICLROnEventManager, interfejs](iclroneventmanager-interface.md)
- [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)
- [IHostControl, interfejs](ihostcontrol-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
