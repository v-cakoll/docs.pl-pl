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
ms.openlocfilehash: 09b4a06892cdc450eed9dead503a990b6f19804e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501511"
---
# <a name="ihostmemorymanager-interface"></a>IHostMemoryManager — Interfejs
Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do udostępniania żądań pamięci wirtualnej za pośrednictwem hosta, zamiast używać standardowych funkcji pamięci wirtualnej Win32.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AcquiredVirtualAddressSpace, metoda](ihostmemorymanager-acquiredvirtualaddressspace-method.md)|Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskało określoną ilość pamięci z systemu operacyjnego.|  
|[CreateMAlloc, metoda](ihostmemorymanager-createmalloc-method.md)|Pobiera wskaźnik interfejsu do wystąpienia [IHostMAlloc](ihostmalloc-interface.md) , które jest używane do żądania alokacji pamięci ze sterty utworzonej przez hosta.|  
|[GetMemoryLoad, metoda](ihostmemorymanager-getmemoryload-method.md)|Pobiera ilość pamięci fizycznej, która jest aktualnie używana, zgłoszoną przez hosta.|  
|[NeedsVirtualAddressSpace, metoda](ihostmemorymanager-needsvirtualaddressspace-method.md)|Powiadamia hosta, że środowisko CLR podejmie próbę użycia określonej pamięci.|  
|[RegisterMemoryNotificationCallback, metoda](ihostmemorymanager-registermemorynotificationcallback-method.md)|Rejestruje wskaźnik do funkcji wywołania zwrotnego, który jest wywoływany przez hosta w celu powiadomienia CLR o bieżącym obciążeniu pamięci na komputerze.|  
|[ReleasedVirtualAddressSpace, metoda](ihostmemorymanager-releasedvirtualaddressspace-method.md)|Powiadamia hosta o zakończeniu środowiska CLR przy użyciu określonej pamięci.|  
|[VirtualAlloc, metoda](ihostmemorymanager-virtualalloc-method.md)|Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualFree, metoda](ihostmemorymanager-virtualfree-method.md)|Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zwalnia, anuluje lub zwalnia i determinuje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualProtect, metoda](ihostmemorymanager-virtualprotect-method.md)|Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która zmienia ochronę w regionie zatwierdzonych stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
|[VirtualQuery, metoda](ihostmemorymanager-virtualquery-method.md)|Służy jako otoka logiczna dla odpowiedniej funkcji Win32, która pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostMemoryManager`Program udostępnia również metody dla środowiska CLR, w których można uzyskać wskaźnik, za pomocą którego należy wykonać żądania pamięci na stercie i uzyskać poziom ciśnienia pamięci w procesie, zgodnie z raportem hosta.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMalloc, interfejs](ihostmalloc-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
