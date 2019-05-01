---
title: EMemoryCriticalLevel — Wyliczenie
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ee8705d00e1f63f69863d0bf8e7d0d9d62807e6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61968613"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel — Wyliczenie
Zawiera wartości, które wskazują wpływ awarii, gdy zażądano alokacji pamięci, ale nie mogą zostać spełnione.  
  
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
|`eAppDomainCritical`|Wskazuje, czy przydział jest istotne w przypadku wykonywania kodu zarządzanego w domenie, który zgłosił żądanie alokacji. Jeśli nie można przydzielić pamięci, środowisko CLR nie gwarantuje, że domena jest nadal można używać. Host decyduje, jaką akcję do wykonania w przypadku alokacja nie mogą zostać spełnione. Można nakazać, środowisko CLR, aby przerwać `AppDomain` automatycznie, lub zezwolenia na jego pozostanie uruchomione przez wywołanie metody w [iclrpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Wskazuje, że przydział ma kluczowe znaczenie dla wykonywania kodu zarządzanego w procesie. Ta wartość jest używana podczas uruchamiania i podczas uruchamiania finalizatorów. Jeśli nie można przydzielić pamięci, środowisko CLR nie może działać w procesie. Jeśli alokacja nie powiedzie się, środowisko CLR skutecznie jest wyłączone. Wszystkie kolejne wywołania do środowiska CLR zakończona niepowodzeniem z HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Wskazuje przydział mają kluczowe znaczenie dla uruchomienia zadania, który zgłosił żądanie alokacji. Jeśli nie można przydzielić pamięci, środowisko CLR nie gwarantuje zadania mogą być wykonywane. W przypadku awarii, środowisko CLR wywołuje <xref:System.Threading.ThreadAbortException> w wątku systemu fizycznego operacji.|  
  
## <a name="remarks"></a>Uwagi  
 Metody alokacji pamięci, które są zdefiniowane w [ihostmemorymanager —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) i [ihostmalloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) interfejsów przyjmować parametr tego typu. W zależności od ważności awarii hosta można zdecydować, czy natychmiast zwraca Niepowodzenie żądania alokacji lub poczekaj, aż mogą zostać zrealizowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRMemoryNotificationCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
