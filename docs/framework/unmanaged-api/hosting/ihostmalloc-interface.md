---
title: IHostMalloc — Interfejs
ms.date: 03/30/2017
api_name:
- IHostMAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc
helpviewer_keywords:
- IHostMAlloc interface [.NET Framework hosting]
ms.assetid: e3c6643b-6fc7-4a99-959d-4b7b4e63fdee
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2a7a29ef1dc85c2ad554995286e5137fcb104be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757641"
---
# <a name="ihostmalloc-interface"></a>IHostMalloc — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby zażądać szczegółowych alokacji ze stosu za pośrednictwem hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-alloc-method.md)|Żądania, że host przydzielić żądanej ilości pamięci sterty.|  
|[DebugAlloc, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-debugalloc-method.md)|Żądania alokacji żądanej ilości pamięci sterty hosta i dodatkowo Śledź, gdzie pamięć została alokowana.|  
|[Free, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-free-method.md)|Zwalnia pamięć, która została przydzielona za pomocą `Alloc` metody.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR pobiera wskaźnik interfejsu do `IHostMalloc` wystąpienia, wywołując [ihostmemorymanager::createmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
