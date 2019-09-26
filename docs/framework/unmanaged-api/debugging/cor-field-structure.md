---
title: COR_FIELD — Struktura
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f857f773f02da25fe6650000be777b8290f5af91
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274061"
---
# <a name="cor_field-structure"></a>COR_FIELD — Struktura
Zawiera informacje dotyczące pola w obiekcie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`token`|`mdFieldDef` Token, który może służyć do uzyskiwania informacji o polu.|  
|`offset`|Przesunięcie, w bajtach, do danych pola w obiekcie.|  
|`id`|Wartość [COR_TYPEID](cor-typeid-structure.md) , która identyfikuje typ tego pola.|  
|`fieldType`|Wartość wyliczenia CorElementType —, która wskazuje typ pola.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
