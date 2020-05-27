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
ms.openlocfilehash: b4c521489f38360d45c2cf8ff3780e057299f0b4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008953"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="a2fda-102">CorUnmanagedCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a2fda-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="a2fda-103">Określa konwencje wywoływania dla niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="a2fda-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2fda-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="a2fda-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a2fda-105">Members</span></span>  
  
|<span data-ttu-id="a2fda-106">Członek</span><span class="sxs-lookup"><span data-stu-id="a2fda-106">Member</span></span>|<span data-ttu-id="a2fda-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a2fda-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="a2fda-108">Konwencja wywoływania języka C.</span><span class="sxs-lookup"><span data-stu-id="a2fda-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="a2fda-109">Standardowa Konwencja wywoływania.</span><span class="sxs-lookup"><span data-stu-id="a2fda-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="a2fda-110">Konwencja wywoływania "This".</span><span class="sxs-lookup"><span data-stu-id="a2fda-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="a2fda-111">Konwencja wywoływania "Fast".</span><span class="sxs-lookup"><span data-stu-id="a2fda-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="a2fda-112">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a2fda-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="a2fda-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a2fda-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="a2fda-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a2fda-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="a2fda-115">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="a2fda-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2fda-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2fda-116">Remarks</span></span>  
 <span data-ttu-id="a2fda-117">Środowisko CLR nie obsługuje konwencji wywoływania "Fast" w .NET Framework w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="a2fda-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2fda-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2fda-118">Requirements</span></span>  
 <span data-ttu-id="a2fda-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2fda-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2fda-120">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a2fda-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a2fda-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2fda-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fda-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2fda-122">See also</span></span>

- [<span data-ttu-id="a2fda-123">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a2fda-123">Metadata Enumerations</span></span>](metadata-enumerations.md)
