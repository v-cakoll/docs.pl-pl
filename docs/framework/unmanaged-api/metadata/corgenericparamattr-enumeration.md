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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450276"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="8bca8-102">CorGenericParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8bca8-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="8bca8-103">Zawiera wartości opisujące parametry <xref:System.Type> dla typów ogólnych, które są używane w wywołaniach [IMetaDataEmit2::D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="8bca8-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bca8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8bca8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="8bca8-105">Members</span><span class="sxs-lookup"><span data-stu-id="8bca8-105">Members</span></span>  
  
|<span data-ttu-id="8bca8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8bca8-106">Member</span></span>|<span data-ttu-id="8bca8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8bca8-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="8bca8-108">WARIANCJA parametrów dotyczy tylko parametrów ogólnych interfejsów i delegatów.</span><span class="sxs-lookup"><span data-stu-id="8bca8-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="8bca8-109">Wskazuje brak wariancji.</span><span class="sxs-lookup"><span data-stu-id="8bca8-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="8bca8-110">Wskazuje kowariancję.</span><span class="sxs-lookup"><span data-stu-id="8bca8-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="8bca8-111">Wskazuje kontrawariancja.</span><span class="sxs-lookup"><span data-stu-id="8bca8-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="8bca8-112">Ograniczenia specjalne mogą dotyczyć dowolnego parametru <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8bca8-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="8bca8-113">Wskazuje, że żadne ograniczenie nie ma zastosowania do parametru <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="8bca8-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="8bca8-114">Wskazuje, że parametr <xref:System.Type> musi być typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="8bca8-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="8bca8-115">Wskazuje, że parametr <xref:System.Type> musi być typem wartości, który nie może być wartością null.</span><span class="sxs-lookup"><span data-stu-id="8bca8-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="8bca8-116">Wskazuje, że parametr <xref:System.Type> musi mieć domyślnego konstruktora publicznego, który nie przyjmuje żadnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="8bca8-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8bca8-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8bca8-117">Requirements</span></span>  
 <span data-ttu-id="8bca8-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bca8-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bca8-119">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="8bca8-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8bca8-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bca8-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bca8-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8bca8-121">See also</span></span>

- [<span data-ttu-id="8bca8-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8bca8-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
