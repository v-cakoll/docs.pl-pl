---
title: COR_GC_THREAD_STATS — Struktura
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431831"
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS — Struktura
Zawiera dla każdego wątku statystyki dotyczące wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`PerThreadAllocation`|Liczba bajtów pamięci przydzielonej w wątku, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpienia. Ta liczba jest ustawiony na wartość 0 zawsze, gdy występuje zero generowania wyrzucania elementów bezużytecznych.|  
|`Flags`|Liczba bajtów podwyższony do wyższych generacji najbardziej aktualnych wyrzucanie elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
