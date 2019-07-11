---
title: COR_PRF_STATIC_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_STATIC_TYPE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_STATIC_TYPE
helpviewer_keywords:
- COR_PRF_STATIC_TYPE enumeration [.NET Framework profiling]
ms.assetid: 441d7809-5b65-41a5-ba64-2910a8008315
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 753c3b38187dd69593dcb0520acef9ce4b137039
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751897"
---
# <a name="corprfstatictype-enumeration"></a>COR_PRF_STATIC_TYPE — Wyliczenie
Wskazuje, czy pole jest statyczna, a jeśli tak, statycznej jakości, która odnosi się do pola. Te wartości można łączyć, używając operacja bitowa lub w celu wskazania, że pole ma wiele różnych klas statycznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum {  
    COR_PRF_FIELD_NOT_A_STATIC = 0x0,  
    COR_PRF_FIELD_APP_DOMAIN_STATIC = 0x1,  
    COR_PRF_FIELD_THREAD_STATIC = 0x2,  
    COR_PRF_FIELD_CONTEXT_STATIC = 0x4,  
    COR_PRF_FIELD_RVA_STATIC = 0x8  
} COR_PRF_STATIC_TYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Pole nie jest statyczne.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Pole nie jest statyczna domeny aplikacji.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Pole nie jest statyczna wątku.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Pole nie jest statyczna kontekstu.|  
|`COR_PRF_FIELD_RVA_STATIC`|To pole jest względnych adresów wirtualnych (RVA) — statyczne.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
