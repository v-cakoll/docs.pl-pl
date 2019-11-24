---
title: CorPinvokeMap — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441562"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="11a52-102">CorPinvokeMap — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="11a52-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="11a52-103">Specifies options for a PInvoke call.</span><span class="sxs-lookup"><span data-stu-id="11a52-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11a52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11a52-104">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="11a52-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="11a52-105">Members</span></span>  
  
|<span data-ttu-id="11a52-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="11a52-106">Member</span></span>|<span data-ttu-id="11a52-107">Opis</span><span class="sxs-lookup"><span data-stu-id="11a52-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="11a52-108">Use each member name as specified.</span><span class="sxs-lookup"><span data-stu-id="11a52-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="11a52-109">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="11a52-110">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="11a52-111">Marshal strings as multiple-byte character strings.</span><span class="sxs-lookup"><span data-stu-id="11a52-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="11a52-112">Marshal strings as Unicode 2-byte characters.</span><span class="sxs-lookup"><span data-stu-id="11a52-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="11a52-113">Automatically marshal strings appropriately for the target operating system.</span><span class="sxs-lookup"><span data-stu-id="11a52-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="11a52-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span><span class="sxs-lookup"><span data-stu-id="11a52-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="11a52-115">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="11a52-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span><span class="sxs-lookup"><span data-stu-id="11a52-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="11a52-117">Do not perform best-fit mapping of Unicode characters.</span><span class="sxs-lookup"><span data-stu-id="11a52-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="11a52-118">In this case, all unmappable characters will be replaced by a ‘?’.</span><span class="sxs-lookup"><span data-stu-id="11a52-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="11a52-119">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="11a52-120">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="11a52-121">Throw an exception when the interop marshaler encounters an unmappable character.</span><span class="sxs-lookup"><span data-stu-id="11a52-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="11a52-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span><span class="sxs-lookup"><span data-stu-id="11a52-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="11a52-123">Reserved</span><span class="sxs-lookup"><span data-stu-id="11a52-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="11a52-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span><span class="sxs-lookup"><span data-stu-id="11a52-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="11a52-125">Reserved</span><span class="sxs-lookup"><span data-stu-id="11a52-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="11a52-126">Use the default platform calling convention.</span><span class="sxs-lookup"><span data-stu-id="11a52-126">Use the default platform calling convention.</span></span> <span data-ttu-id="11a52-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="11a52-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="11a52-128">Use the `Cdecl` calling convention.</span><span class="sxs-lookup"><span data-stu-id="11a52-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="11a52-129">In this case, the caller cleans the stack.</span><span class="sxs-lookup"><span data-stu-id="11a52-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="11a52-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span><span class="sxs-lookup"><span data-stu-id="11a52-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="11a52-131">Use the `StdCall` calling convention.</span><span class="sxs-lookup"><span data-stu-id="11a52-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="11a52-132">In this case, the callee cleans the stack.</span><span class="sxs-lookup"><span data-stu-id="11a52-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="11a52-133">This is the default convention for calling unmanaged functions with platform invoke.</span><span class="sxs-lookup"><span data-stu-id="11a52-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="11a52-134">Use the `ThisCall` calling convention.</span><span class="sxs-lookup"><span data-stu-id="11a52-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="11a52-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span><span class="sxs-lookup"><span data-stu-id="11a52-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="11a52-136">Other parameters are pushed on the stack.</span><span class="sxs-lookup"><span data-stu-id="11a52-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="11a52-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span><span class="sxs-lookup"><span data-stu-id="11a52-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="11a52-138">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="11a52-139">Reserved.</span><span class="sxs-lookup"><span data-stu-id="11a52-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="11a52-140">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11a52-140">Requirements</span></span>  
 <span data-ttu-id="11a52-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11a52-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11a52-142">**Header:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="11a52-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="11a52-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11a52-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11a52-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11a52-144">See also</span></span>

- [<span data-ttu-id="11a52-145">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="11a52-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
