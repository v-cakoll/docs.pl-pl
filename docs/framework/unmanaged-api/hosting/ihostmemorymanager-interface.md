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
ms.openlocfilehash: d3edae4cb112f46643734c5f1612d9df36ad47e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager — Interfejs
Udostępnia metody, które umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do żądania pamięci wirtualnej za pośrednictwem hosta, zamiast używać standardowych funkcji Win32 w pamięci wirtualnej.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskał określonego pamięci systemu operacyjnego.|  
|[CreateMAlloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|Pobiera wskaźnika interfejsu do [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) wystąpienie, które jest używane do żądania alokacji pamięci z sterty utworzone przez hosta.|  
|[GetMemoryLoad, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|Pobiera ilość pamięci fizycznej, która jest aktualnie używana, zgłoszonej przez hosta.|  
|[NeedsVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|Powiadamia host czy CLR będzie próbować używać pamięci określony.|  
|[RegisterMemoryNotificationCallback, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|Rejestruje wskaźnika do funkcji wywołania zwrotnego, która wywołuje hosta powiadomiono CLR bieżącego obciążenia pamięci na komputerze.|  
|[ReleasedVirtualAddressSpace, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|Powiadamia hosta CLR zostało zakończone, przy użyciu określonego pamięci.|  
|[VirtualAlloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|Służy jako otoka logiczne dla odpowiedniej funkcji Win32, rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualFree, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|Służy jako otoka logiczne dla odpowiedniej funkcji Win32, co zwalnia, decommits, lub zwalnia i decommits region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualProtect, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|Służy jako otoka logiczne dla odpowiedniej funkcji Win32 zmienia ochrony obszaru zatwierdzone stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualQuery, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|Służy jako otoka logiczne dla odpowiedniej funkcji Win32 pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostMemoryManager` udostępnia metody dla CLR można uzyskać wskaźnika za pośrednictwem której na wysyłanie żądań pamięci na stosie, a także aby uzyskać poziom wykorzystania pamięci w procesie zgłoszonej przez hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
