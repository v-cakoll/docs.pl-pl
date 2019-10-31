---
title: IDENTITY_ATTRIBUTE — Struktura
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107987"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE — Struktura
Zawiera informacje o atrybucie metadanych dotyczące wystąpienia [IDefinitionIdentity —](idefinitionidentity-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pszNamespace`|Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera przestrzeń nazw, w której znajduje się atrybut.|  
|`pszName`|Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera nazwę atrybutu.|  
|`pszValue`|Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera wartość atrybutu.|  
  
## <a name="remarks"></a>Uwagi  
 Struktura `IDENTITY_ATTRIBUTE` zawiera trzy wskaźniki do ciągów znaków zakończonych znakiem null. Te trzy ciągi opisują jeden atrybut.  
  
 Wystąpienie struktury `IDENTITY_ATTRIBUTE` jest skojarzone z wystąpieniem struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . Struktura `IDENTITY_ATTRIBUTE` zawiera rzeczywiste ciągi, a odpowiednia struktura `IDENTITY_ATTRIBUTE_BLOB` wyświetla przesunięcia na trzy ciągi wymienione w strukturze `IDENTITY_ATTRIBUTE`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IDefinitionIdentity, interfejs](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB, struktura](identity-attribute-blob-structure.md)
- [Łączenie — struktury](fusion-structures.md)
