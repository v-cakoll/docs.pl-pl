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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59178454"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="2db8a-102">CorUnmanagedCallingConvention — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2db8a-102">CorUnmanagedCallingConvention Enumeration</span></span>
<span data-ttu-id="2db8a-103">Określa konwencji wywoływania niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="2db8a-103">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db8a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2db8a-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2db8a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2db8a-105">Members</span></span>  
  
|<span data-ttu-id="2db8a-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2db8a-106">Member</span></span>|<span data-ttu-id="2db8a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2db8a-107">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="2db8a-108">Konwencja wywoływania języka C.</span><span class="sxs-lookup"><span data-stu-id="2db8a-108">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="2db8a-109">Standardowej konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="2db8a-109">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="2db8a-110">"To" Konwencji wywołania.</span><span class="sxs-lookup"><span data-stu-id="2db8a-110">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="2db8a-111">Konwencja wywoływania "fast".</span><span class="sxs-lookup"><span data-stu-id="2db8a-111">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="2db8a-112">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="2db8a-112">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="2db8a-113">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="2db8a-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="2db8a-114">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="2db8a-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="2db8a-115">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="2db8a-115">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2db8a-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2db8a-116">Remarks</span></span>  
 <span data-ttu-id="2db8a-117">Środowisko CLR nie obsługuje "fast" Konwencja wywoływania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="2db8a-117">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db8a-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2db8a-118">Requirements</span></span>  
 <span data-ttu-id="2db8a-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2db8a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2db8a-120">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="2db8a-120">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="2db8a-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2db8a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db8a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2db8a-122">See also</span></span>

- [<span data-ttu-id="2db8a-123">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="2db8a-123">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
