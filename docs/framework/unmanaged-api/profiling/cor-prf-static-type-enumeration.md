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
ms.openlocfilehash: 880c9bd186d6cb2acb277e9cc55d3063fb8d51d8
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867041"
---
# <a name="cor_prf_static_type-enumeration"></a>COR_PRF_STATIC_TYPE — Wyliczenie
Wskazuje, czy pole jest statyczne i, jeśli tak, statyczna jakość stosowana do pola. Te wartości można łączyć za pomocą bitowego lub operacji, aby wskazać, że pole ma wiele różnych klas statycznych.  
  
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
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Pole jest domeną aplikacji — static.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Pole jest statyczne wątku.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Pole jest kontekst-static.|  
|`COR_PRF_FIELD_RVA_STATIC`|Pole jest względnym adresem wirtualnym (RVA) — static.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
