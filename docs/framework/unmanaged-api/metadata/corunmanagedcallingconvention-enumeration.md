---
title: "CorUnmanagedCallingConvention — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorUnmanagedCallingConvention
api_location: mscoree.dll
api_type: COM
f1_keywords: CorUnmanagedCallingConvention
helpviewer_keywords: CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f66cb036de8450d4c1b3431b92487260956d47f0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="119d3-102">CorUnmanagedCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="119d3-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="119d3-103">Określa konwencji wywoływania dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="119d3-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="119d3-104">Syntax</span></span>  
  
```  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="119d3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="119d3-105">Members</span></span>  
  
|<span data-ttu-id="119d3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="119d3-106">Member</span></span>|<span data-ttu-id="119d3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="119d3-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="119d3-108">Konwencja wywoływania języka C.</span><span class="sxs-lookup"><span data-stu-id="119d3-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="119d3-109">Standardowej konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="119d3-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="119d3-110">"This" Konwencji wywołania.</span><span class="sxs-lookup"><span data-stu-id="119d3-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="119d3-111">"Fast" konwencję wywołania.</span><span class="sxs-lookup"><span data-stu-id="119d3-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="119d3-112">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="119d3-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="119d3-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="119d3-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="119d3-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="119d3-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="119d3-115">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="119d3-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="119d3-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="119d3-116">Remarks</span></span>  
 <span data-ttu-id="119d3-117">Środowisko CLR nie obsługuje "fast" Konwencja wywoływania w programie .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="119d3-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119d3-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="119d3-118">Requirements</span></span>  
 <span data-ttu-id="119d3-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119d3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119d3-120">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="119d3-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="119d3-121">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119d3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119d3-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="119d3-122">See Also</span></span>  
 [<span data-ttu-id="119d3-123">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="119d3-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
