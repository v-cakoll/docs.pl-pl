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
ms.openlocfilehash: 80d72aefc736054afcee152c55e941c0f8f3c6a8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500770"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`COR_PRF_FIELD_NOT_A_STATIC`|Pole nie jest statyczne.|  
|`COR_PRF_FIELD_APP_DOMAIN_STATIC`|Pole jest domeną aplikacji — static.|  
|`COR_PRF_FIELD_THREAD_STATIC`|Pole jest statyczne wątku.|  
|`COR_PRF_FIELD_CONTEXT_STATIC`|Pole jest kontekst-static.|  
|`COR_PRF_FIELD_RVA_STATIC`|Pole jest względnym adresem wirtualnym (RVA) — static.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profilowanie — wyliczenia](profiling-enumerations.md)
