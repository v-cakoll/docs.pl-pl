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
ms.openlocfilehash: ea84b742c901ba58a3bb730f1f5033a0d90610ce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007380"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr — Wyliczenie
Zawiera wartości opisujące <xref:System.Type> parametry typów ogólnych, które są używane w wywołaniach [IMetaDataEmit2::D efinegenericparam](imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|WARIANCJA parametrów dotyczy tylko parametrów ogólnych interfejsów i delegatów.|  
|`gpNonVariant`|Wskazuje brak wariancji.|  
|`gpCovariant`|Wskazuje kowariancję.|  
|`gpContravariant`|Wskazuje kontrawariancja.|  
|`gpSpecialConstraintMask`|Ograniczenia specjalne mogą dotyczyć dowolnego <xref:System.Type> parametru.|  
|`gpNoSpecialConstraint`|Wskazuje, że żadne ograniczenie nie ma zastosowania do <xref:System.Type> parametru.|  
|`gpReferenceTypeConstraint`|Wskazuje, że <xref:System.Type> parametr musi być typem referencyjnym.|  
|`gpNotNullableValueTypeConstraint`|Wskazuje, że <xref:System.Type> parametr musi być typem wartości, który nie może być wartością null.|  
|`gpDefaultConstructorConstraint`|Wskazuje, że <xref:System.Type> parametr musi mieć domyślny konstruktor publiczny, który nie przyjmuje żadnych parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
