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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aa9b84c9e16811f799a3cd2ad096508db3f7d34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045797"
---
# <a name="corgenericparamattr-enumeration"></a>CorGenericParamAttr — Wyliczenie
Zawiera wartości, które opisują <xref:System.Type> parametrów dla typów ogólnych, jako używane wywołania [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).  
  
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
|`gpVarianceMask`|Parametr wariancja dotyczy tylko parametrów ogólnych interfejsów i delegatów.|  
|`gpNonVariant`|Wskazuje brak wariancji.|  
|`gpCovariant`|Wskazuje KOWARIANCJA.|  
|`gpContravariant`|Wskazuje, kontrawariancja.|  
|`gpSpecialConstraintMask`|Specjalne ograniczenia można zastosować do dowolnego <xref:System.Type> parametru.|  
|`gpNoSpecialConstraint`|Wskazuje, że nie ograniczenie ma zastosowanie do <xref:System.Type> parametru.|  
|`gpReferenceTypeConstraint`|Oznacza to, że <xref:System.Type> parametr musi być typem referencyjnym.|  
|`gpNotNullableValueTypeConstraint`|Oznacza to, że <xref:System.Type> parametr musi być typem wartości, która nie może mieć wartości null.|  
|`gpDefaultConstructorConstraint`|Oznacza to, że <xref:System.Type> parametr musi mieć domyślnego konstruktora publicznego, który nie przyjmuje żadnych parametrów.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
