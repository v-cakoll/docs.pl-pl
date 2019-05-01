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
ms.openlocfilehash: ff308a81282a1cc14c35583daf9cbb057149e556
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905440"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="f1fb1-102">CorUnmanagedCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f1fb1-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="f1fb1-103">Określa konwencji wywoływania niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1fb1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1fb1-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f1fb1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f1fb1-105">Members</span></span>  
  
|<span data-ttu-id="f1fb1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f1fb1-106">Member</span></span>|<span data-ttu-id="f1fb1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f1fb1-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="f1fb1-108">Konwencja wywoływania języka C.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="f1fb1-109">Standardowej konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="f1fb1-110">"To" Konwencji wywołania.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="f1fb1-111">Konwencja wywoływania "fast".</span><span class="sxs-lookup"><span data-stu-id="f1fb1-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="f1fb1-112">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="f1fb1-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="f1fb1-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="f1fb1-115">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1fb1-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1fb1-116">Remarks</span></span>  
 <span data-ttu-id="f1fb1-117">Środowisko CLR nie obsługuje "fast" Konwencja wywoływania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="f1fb1-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1fb1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1fb1-118">Requirements</span></span>  
 <span data-ttu-id="f1fb1-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1fb1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1fb1-120">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="f1fb1-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f1fb1-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1fb1-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fb1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1fb1-122">See also</span></span>

- [<span data-ttu-id="f1fb1-123">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f1fb1-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
