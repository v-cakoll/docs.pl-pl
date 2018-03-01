---
title: "CorGenericParamAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e40613d790baed5bd89bee1e1f5ca57043bfe76a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr — Wyliczenie
Zawiera wartości, które opisują <xref:System.Type> parametrów dla typów ogólnych jako używanych w wywołaniach [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`gpVarianceMask`|Parametr wariancję dotyczy tylko parametrów ogólnych interfejsów i delegatów.|  
|`gpNonVariant`|Wskazuje brak wariancji.|  
|`gpCovariant`|Wskazuje KOWARIANCJA.|  
|`gpContravariant`|Wskazuje kontrawariancja.|  
|`gpSpecialConstraintMask`|Ograniczeń specjalnych można stosować do dowolnych <xref:System.Type> parametru.|  
|`gpNoSpecialConstraint`|Wskazuje, że ograniczenie nie dotyczy <xref:System.Type> parametru.|  
|`gpReferenceTypeConstraint`|Oznacza to, że <xref:System.Type> parametr musi być typem referencyjnym.|  
|`gpNotNullableValueTypeConstraint`|Oznacza to, że <xref:System.Type> parametr musi być typem wartości, która nie może być wartością null.|  
|`gpDefaultConstructorConstraint`|Oznacza to, że <xref:System.Type> parametr musi mieć domyślnego konstruktora publicznego, który nie przyjmuje żadnych parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
