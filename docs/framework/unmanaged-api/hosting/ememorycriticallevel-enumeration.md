---
title: "EMemoryCriticalLevel — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b15a6786cb99a64d441d7e05fb91cd8ff0f3af92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel — Wyliczenie
Zawiera wartości, które wskazują wpływ awarii podczas alokacji pamięci wysłano żądanie, ale nie mogą zostać spełnione.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`eAppDomainCritical`|Wskazuje, że przydział ma decydujące znaczenie dla wykonywania kodu zarządzanego w domenie, do której wysłano żądanie alokacji. Jeśli nie można przydzielić pamięci, CLR nie może zagwarantować, że domena jest nadal można używać. Host decyduje o tym, jakie działania w sytuacji, gdy nie mogą być spełnione alokacji. Może spowodować, żeby CLR aby przerwać `AppDomain` automatycznie, lub zezwalanie na kontynuowanie działania przez wywołanie metody na [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Wskazuje, że przydział jest krytyczne w wykonywaniu kodu zarządzanego w procesie. Ta wartość jest używana podczas uruchamiania i podczas uruchamiania finalizatory. Jeśli nie można przydzielić pamięci, CLR nie może działać w procesie. Jeśli alokacja nie powiedzie się, CLR skutecznie jest wyłączone. Wszystkie kolejne wywołania do środowiska CLR się niepowodzeniem z HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Wskazuje, że przydział jest krytyczne do uruchomienia zadania, który zgłosił żądanie alokacji. Jeśli nie można przydzielić pamięci, CLR nie może zagwarantować, można wykonać zadania. W przypadku awarii, zgłasza CLR <xref:System.Threading.ThreadAbortException> w wątku systemu fizycznego operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Metody alokacji pamięci, które są zdefiniowane w [IHostMemoryManager](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) i [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfejsy zająć parametr tego typu. W zależności od ważności awarii hosta można zdecydować, czy niepowodzenie żądanie alokacji natychmiast lub poczekać, aż można spełnić.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRMemoryNotificationCallback — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
