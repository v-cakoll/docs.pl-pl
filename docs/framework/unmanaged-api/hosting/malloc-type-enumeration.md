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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1c3fd9155761528b9203a5c69dee0bde16327f7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779339"
---
# <a name="malloctype-enumeration"></a>MALLOC_TYPE — Wyliczenie
Zawiera wartości, które określają właściwości pamięci, która jest przydzielane.  
  
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
|`MALLOC_EXECUTABLE`|Ilość przydzielonej pamięci może zawierać plik wykonywalny.|  
|`MALLOC_THREADSAFE`|Ilość przydzielonej pamięci jest metodą o bezpiecznych wątkach. Oznacza to, że pamięć jest możliwy przez wiele wątków, bez żadnej synchronizacji.<br /><br /> Jeśli ta flaga nie jest ustawiona, wywołania do obiektu, trzeba go serializować.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — wyliczenia](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
