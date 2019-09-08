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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796486"
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
 `IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźniki do ciągów znaków zakończonych znakiem null. Te trzy ciągi opisują jeden atrybut.  
  
 Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzone z wystąpieniem struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . Struktura zawiera rzeczywiste ciągi, a odpowiednia `IDENTITY_ATTRIBUTE_BLOB` struktura zawiera listę przesunięć do `IDENTITY_ATTRIBUTE` trzech ciągów wymienionych w strukturze. `IDENTITY_ATTRIBUTE`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IDefinitionIdentity, interfejs](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB, struktura](identity-attribute-blob-structure.md)
- [Łączenie — struktury](fusion-structures.md)
