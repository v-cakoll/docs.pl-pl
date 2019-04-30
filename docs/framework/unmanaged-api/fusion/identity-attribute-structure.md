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
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698047"
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE — Struktura
Zawiera informacje o atrybutach metadane dotyczące [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
