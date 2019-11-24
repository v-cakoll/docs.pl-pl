---
title: CorCallingConvention — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 9d4690cb6adedc77717e577d409cb52b18b1b5ca
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443836"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="c816e-102">CorCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c816e-102">CorCallingConvention Enumeration</span></span>
<span data-ttu-id="c816e-103">Contains values that describe the types of calling conventions that are made in managed code.</span><span class="sxs-lookup"><span data-stu-id="c816e-103">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c816e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c816e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="c816e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c816e-105">Members</span></span>  
  
|<span data-ttu-id="c816e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c816e-106">Member</span></span>|<span data-ttu-id="c816e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c816e-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="c816e-108">Indicates a default calling convention.</span><span class="sxs-lookup"><span data-stu-id="c816e-108">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="c816e-109">Indicates that the method takes a variable number of parameters.</span><span class="sxs-lookup"><span data-stu-id="c816e-109">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="c816e-110">Indicates that the call is to a field.</span><span class="sxs-lookup"><span data-stu-id="c816e-110">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="c816e-111">Indicates that the call is to a local method.</span><span class="sxs-lookup"><span data-stu-id="c816e-111">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="c816e-112">Indicates that the call is to a property.</span><span class="sxs-lookup"><span data-stu-id="c816e-112">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="c816e-113">Indicates that the call is unmanaged.</span><span class="sxs-lookup"><span data-stu-id="c816e-113">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="c816e-114">Indicates a generic method instantiation.</span><span class="sxs-lookup"><span data-stu-id="c816e-114">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="c816e-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span><span class="sxs-lookup"><span data-stu-id="c816e-115">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="c816e-116">Describes an invalid 4-bit value.</span><span class="sxs-lookup"><span data-stu-id="c816e-116">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="c816e-117">Indicates that the calling convention is described by the bottom four bits.</span><span class="sxs-lookup"><span data-stu-id="c816e-117">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="c816e-118">Indicates that the top bit describes a `this` parameter.</span><span class="sxs-lookup"><span data-stu-id="c816e-118">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="c816e-119">Indicates that a `this` parameter is explicitly described in the signature.</span><span class="sxs-lookup"><span data-stu-id="c816e-119">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="c816e-120">Indicates a generic method signature with an explicit number of type arguments.</span><span class="sxs-lookup"><span data-stu-id="c816e-120">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="c816e-121">This precedes an ordinary parameter count.</span><span class="sxs-lookup"><span data-stu-id="c816e-121">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c816e-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c816e-122">Requirements</span></span>  
 <span data-ttu-id="c816e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c816e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c816e-124">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c816e-124">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c816e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c816e-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c816e-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c816e-126">See also</span></span>

- [<span data-ttu-id="c816e-127">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="c816e-127">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
