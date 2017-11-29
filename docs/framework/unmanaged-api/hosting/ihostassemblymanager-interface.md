---
title: "IHostAssemblyManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAssemblyManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAssemblyManager
helpviewer_keywords: IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b3761063201a48303884fdecddddf02558cd4e5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager — Interfejs
Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyStore — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getassemblystore-method.md)|Pobiera wskaźnika interfejsu do [IHostAssemblyStore](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md) reprezentujący listę zestawów załadowanych przez hosta.|  
|[GetNonHostStoreAssemblies — metoda](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-getnonhoststoreassemblies-method.md)|Pobiera wskaźnika interfejsu do [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) reprezentujący listę zestawów, które host oczekuje można załadować środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagane do zaimplementowania `IHostAssemblyManager` lub `IHostAssemblyStore`. Jeśli host wdrożenia `IHostAssemblyManager`, musi implementować też `IHostAssemblyStore`.  
  
 Środowisko uruchomieniowe kwerendy o `IHostAssemblyManager` przez wywołanie metody [IHostControl::GetHostManager](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` z IID_IHostAssemblyManager.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [IHostAssemblyStore — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
