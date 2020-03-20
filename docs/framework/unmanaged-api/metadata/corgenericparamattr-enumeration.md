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
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="1ad48-102">CorGenericParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1ad48-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="1ad48-103">Zawiera wartości <xref:System.Type> opisujące parametry typów ogólnych, używane w wywołaniach [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="1ad48-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ad48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ad48-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="1ad48-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1ad48-105">Members</span></span>  
  
|<span data-ttu-id="1ad48-106">Członek</span><span class="sxs-lookup"><span data-stu-id="1ad48-106">Member</span></span>|<span data-ttu-id="1ad48-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1ad48-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="1ad48-108">Wariancja parametrów ma zastosowanie tylko do parametrów ogólnych dla interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="1ad48-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="1ad48-109">Wskazuje brak wariancji.</span><span class="sxs-lookup"><span data-stu-id="1ad48-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="1ad48-110">Wskazuje kowariancję.</span><span class="sxs-lookup"><span data-stu-id="1ad48-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="1ad48-111">Wskazuje kontrawarancję.</span><span class="sxs-lookup"><span data-stu-id="1ad48-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="1ad48-112">Specjalne ograniczenia mogą mieć <xref:System.Type> zastosowanie do dowolnego parametru.</span><span class="sxs-lookup"><span data-stu-id="1ad48-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="1ad48-113">Wskazuje, że do parametru <xref:System.Type> nie ma zastosowania żadne ograniczenie.</span><span class="sxs-lookup"><span data-stu-id="1ad48-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="1ad48-114">Wskazuje, że <xref:System.Type> parametr musi być typem odwołania.</span><span class="sxs-lookup"><span data-stu-id="1ad48-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="1ad48-115">Wskazuje, że <xref:System.Type> parametr musi być typem wartości, która nie może być wartością null.</span><span class="sxs-lookup"><span data-stu-id="1ad48-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="1ad48-116">Wskazuje, że <xref:System.Type> parametr musi mieć domyślny konstruktor publiczny, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="1ad48-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ad48-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ad48-117">Requirements</span></span>  
 <span data-ttu-id="1ad48-118">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad48-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ad48-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="1ad48-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1ad48-120">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad48-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ad48-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ad48-121">See also</span></span>

- [<span data-ttu-id="1ad48-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="1ad48-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
