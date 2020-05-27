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
ms.openlocfilehash: 630fe4e79b369bfdefc19be72780f1893090895e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008459"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|Przydzieloną pamięć może zawierać plik wykonywalny.|  
|`MALLOC_THREADSAFE`|Przydzieloną pamięć jest bezpieczna wątkowo. Oznacza to, że pamięć może być dostępna przez wiele wątków bez żadnej synchronizacji.<br /><br /> Jeśli ta flaga nie jest ustawiona, wywołania na obiekcie muszą być serializowane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting — Wyliczenia](hosting-enumerations.md)
