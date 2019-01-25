---
title: CorUnmanagedCallingConvention — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a1ee9ab1649a832b6daefc96049d68850f3bc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555560"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="bd8f0-102">CorUnmanagedCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bd8f0-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="bd8f0-103">Określa konwencji wywoływania niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd8f0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bd8f0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bd8f0-105">Members</span></span>  
  
|<span data-ttu-id="bd8f0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bd8f0-106">Member</span></span>|<span data-ttu-id="bd8f0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bd8f0-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="bd8f0-108">Konwencja wywoływania języka C.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="bd8f0-109">Standardowej konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="bd8f0-110">"To" Konwencji wywołania.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="bd8f0-111">Konwencja wywoływania "fast".</span><span class="sxs-lookup"><span data-stu-id="bd8f0-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="bd8f0-112">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="bd8f0-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="bd8f0-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="bd8f0-115">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8f0-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd8f0-116">Remarks</span></span>  
 <span data-ttu-id="bd8f0-117">Środowisko CLR nie obsługuje "fast" Konwencja wywoływania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="bd8f0-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8f0-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd8f0-118">Requirements</span></span>  
 <span data-ttu-id="bd8f0-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd8f0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd8f0-120">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="bd8f0-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="bd8f0-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd8f0-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8f0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd8f0-122">See also</span></span>
- [<span data-ttu-id="bd8f0-123">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="bd8f0-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
