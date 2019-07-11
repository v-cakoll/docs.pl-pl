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
ms.openlocfilehash: de1646cdbc11369b43a821d8b762879d1df7ed2e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751537"
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE — Struktura
Zawiera informacje o atrybutach metadane dotyczące [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.  
  
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
|`pszNamespace`|Wskaźnik do ciągu zakończonego znakiem null, zawierającą przestrzeń nazw atrybut jest.|  
|`pszName`|Wskaźnik do ciągu zakończonego znakiem null, zawierający nazwę atrybutu.|  
|`pszValue`|Wskaźnik do ciągu zakończonego znakiem null, zawierający wartość atrybutu.|  
  
## <a name="remarks"></a>Uwagi  
 `IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźnikami do ciągów znaków zakończony znakiem null. Te trzy ciągi opisują jeden atrybut.  
  
 Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury. `IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiedni `IDENTITY_ATTRIBUTE_BLOB` struktura zawiera listę przesunięć na trzy ciągi na liście `IDENTITY_ATTRIBUTE` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IDefinitionIdentity, interfejs](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB, struktura](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [Łączenie — struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
