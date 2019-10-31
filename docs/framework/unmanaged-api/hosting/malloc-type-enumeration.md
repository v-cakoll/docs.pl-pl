---
title: MALLOC_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: 16f56809b4db159c71b06b3bb9d969f8a8f8fc54
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090824"
---
# <a name="malloc_type-enumeration"></a>MALLOC_TYPE — Wyliczenie
Zawiera wartości określające charakterystyki przydzielenia pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|Przydzieloną pamięć może zawierać plik wykonywalny.|  
|`MALLOC_THREADSAFE`|Przydzieloną pamięć jest bezpieczna wątkowo. Oznacza to, że pamięć może być dostępna przez wiele wątków bez żadnej synchronizacji.<br /><br /> Jeśli ta flaga nie jest ustawiona, wywołania na obiekcie muszą być serializowane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
