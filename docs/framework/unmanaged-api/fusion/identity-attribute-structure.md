---
title: "IDENTITY_ATTRIBUTE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE — Struktura
Zawiera informacje o atrybutach metadane dotyczące [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.  
  
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
|`pszNamespace`|Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera przestrzeń nazw atrybutu jest w.|  
|`pszName`|Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera nazwę atrybutu.|  
|`pszValue`|Wskaźnik na ciąg znaków zakończony znakiem null zawierającym wartość atrybutu.|  
  
## <a name="remarks"></a>Uwagi  
 `IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźniki do ciągów znaków zakończony znakiem null. Te trzy ciągi opisano jeden atrybut.  
  
 Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury. `IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiadający mu `IDENTITY_ATTRIBUTE_BLOB` przesunięcia na trzy ciągi, na liście wymieniono struktury `IDENTITY_ATTRIBUTE` struktury.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IDefinitionIdentity, interfejs](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [IDENTITY_ATTRIBUTE_BLOB, struktura](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [Łączenie — struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
