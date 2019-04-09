---
title: IHostMemoryManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137361"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do wysyłania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskała określonego pamięci systemu operacyjnego.|  
|[CreateMAlloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Pobiera wskaźnik interfejsu do [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które służy do żądania alokacji pamięci ze stosu, utworzone przez hosta.|  
|[GetMemoryLoad, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Pobiera ilość pamięci fizycznej, który jest aktualnie używany, zgłoszonej przez hosta.|  
|[NeedsVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Powiadamia hosta, środowisko CLR jest zamierza podejmują próbę użycia określonego pamięci.|  
|[RegisterMemoryNotificationCallback, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta w celu powiadamiania CLR bieżące obciążenie pamięci na komputerze.|  
|[ReleasedVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Powiadamia hosta, że CLR została zakończona, użycie pamięci określonej.|  
|[VirtualAlloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która rezerwuje lub zwalnia region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualFree, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Służy jako logiczne otoki dla odpowiedniej funkcji Win32, które zwalnia, anuluje, zwalnia lub anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualProtect, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która zmienia ochronę na region stron zadeklarowanej w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualQuery, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Służy jako logiczne otoki dla odpowiedniej funkcji Win32, która pobiera informacje o zakres stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostMemoryManager` zapewnia także metody dla środowiska CLR można uzyskać wskaźnika za pomocą którego propozycji dotyczących pamięci na stosie i uzyskać poziom wykorzystania pamięci w procesie zgłoszonej przez hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMalloc — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
