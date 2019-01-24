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
ms.openlocfilehash: 3f453867f6b46265fdbf567b4374ddc64b4efe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563902"
---
# <a name="corgcthreadstats-structure"></a>COR_GC_THREAD_STATS — Struktura
Zawiera statystyki wątku odnoszących się do wyrzucania elementów bezużytecznych.  
  
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
|`PerThreadAllocation`|Liczba bajtów pamięci przydzielonej na wątek, który jest skojarzony z bieżącym `COR_GC_THREAD_STATS` wystąpienia. Ta liczba jest ustawiony na wartość 0, każdym razem, gdy występuje zero generacji wyrzucania elementów bezużytecznych.|  
|`Flags`|Liczba bajtów podwyższony do wyższej generacji najbardziej aktualnych wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
 [Iclrtask::getmemstats —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) przyjmuje parametr wyjściowy typu `COR_GC_THREAD_STATS`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** GCHost.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, struktury](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
