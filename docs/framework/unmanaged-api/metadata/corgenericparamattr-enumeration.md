---
title: CorGenericParamAttr — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176178"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr — Wyliczenie
Zawiera wartości <xref:System.Type> opisujące parametry typów ogólnych, używane w wywołaniach [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
|Członek|Opis|  
|------------|-----------------|  
|`gpVarianceMask`|Wariancja parametrów ma zastosowanie tylko do parametrów ogólnych dla interfejsów i delegatów.|  
|`gpNonVariant`|Wskazuje brak wariancji.|  
|`gpCovariant`|Wskazuje kowariancję.|  
|`gpContravariant`|Wskazuje kontrawarancję.|  
|`gpSpecialConstraintMask`|Specjalne ograniczenia mogą mieć <xref:System.Type> zastosowanie do dowolnego parametru.|  
|`gpNoSpecialConstraint`|Wskazuje, że do parametru <xref:System.Type> nie ma zastosowania żadne ograniczenie.|  
|`gpReferenceTypeConstraint`|Wskazuje, że <xref:System.Type> parametr musi być typem odwołania.|  
|`gpNotNullableValueTypeConstraint`|Wskazuje, że <xref:System.Type> parametr musi być typem wartości, która nie może być wartością null.|  
|`gpDefaultConstructorConstraint`|Wskazuje, że <xref:System.Type> parametr musi mieć domyślny konstruktor publiczny, który nie przyjmuje żadnych parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
