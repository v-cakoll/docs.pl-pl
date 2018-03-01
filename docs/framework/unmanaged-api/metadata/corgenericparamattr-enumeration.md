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
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="d22ac-102">CorGenericParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d22ac-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="d22ac-103">Zawiera wartości, które opisują <xref:System.Type> parametrów dla typów ogólnych jako używanych w wywołaniach [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="d22ac-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d22ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d22ac-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d22ac-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d22ac-105">Members</span></span>  
  
|<span data-ttu-id="d22ac-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d22ac-106">Member</span></span>|<span data-ttu-id="d22ac-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d22ac-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="d22ac-108">Parametr wariancję dotyczy tylko parametrów ogólnych interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="d22ac-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="d22ac-109">Wskazuje brak wariancji.</span><span class="sxs-lookup"><span data-stu-id="d22ac-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="d22ac-110">Wskazuje KOWARIANCJA.</span><span class="sxs-lookup"><span data-stu-id="d22ac-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="d22ac-111">Wskazuje kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="d22ac-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="d22ac-112">Ograniczeń specjalnych można stosować do dowolnych <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="d22ac-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="d22ac-113">Wskazuje, że ograniczenie nie dotyczy <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="d22ac-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="d22ac-114">Oznacza to, że <xref:System.Type> parametr musi być typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="d22ac-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="d22ac-115">Oznacza to, że <xref:System.Type> parametr musi być typem wartości, która nie może być wartością null.</span><span class="sxs-lookup"><span data-stu-id="d22ac-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="d22ac-116">Oznacza to, że <xref:System.Type> parametr musi mieć domyślnego konstruktora publicznego, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="d22ac-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d22ac-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d22ac-117">Requirements</span></span>  
 <span data-ttu-id="d22ac-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d22ac-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d22ac-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d22ac-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d22ac-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d22ac-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d22ac-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d22ac-121">See Also</span></span>  
 [<span data-ttu-id="d22ac-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d22ac-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
