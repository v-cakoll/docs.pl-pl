---
title: "CorPinvokeMap — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPinvokeMap
helpviewer_keywords: CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9c6e1a49d18cde768884ab3d92eaa6593e2955c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="487cb-102">CorPinvokeMap — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="487cb-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="487cb-103">Określa opcje dla wywołania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="487cb-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="487cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="487cb-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="487cb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="487cb-105">Members</span></span>  
  
|<span data-ttu-id="487cb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="487cb-106">Member</span></span>|<span data-ttu-id="487cb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="487cb-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="487cb-108">Użyj nazwy elementów członkowskich określonych.</span><span class="sxs-lookup"><span data-stu-id="487cb-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="487cb-109">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="487cb-110">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="487cb-111">Kierowanie ciągi jako ciągi wielu bajtowych wartości znakowych.</span><span class="sxs-lookup"><span data-stu-id="487cb-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="487cb-112">Kierowanie ciągów Unicode 2-bajtowych znaków.</span><span class="sxs-lookup"><span data-stu-id="487cb-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="487cb-113">Automatyczne kierowanie ciągów odpowiednio dla docelowego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="487cb-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="487cb-114">Wartość domyślna to Unicode na systemu Windows NT, Windows 2000, Windows XP i z rodziny Windows Server 2003; Wartość domyślna to ANSI w systemach Windows 98 i systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="487cb-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="487cb-115">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="487cb-116">Przeprowadź mapowanie najlepszego dopasowania znaków Unicode, których brakuje dokładnego dopasowania w zestawie znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="487cb-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="487cb-117">Nie wykonuj mapowanie najlepszego dopasowania znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="487cb-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="487cb-118">W takim przypadku zostanie zastąpiona zmapować znakami "?".</span><span class="sxs-lookup"><span data-stu-id="487cb-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="487cb-119">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="487cb-120">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="487cb-121">Zgłoś wyjątek, gdy znak zmapować napotka międzyoperacyjnego organizatora.</span><span class="sxs-lookup"><span data-stu-id="487cb-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="487cb-122">Nie Zgłoś wyjątek, gdy znak zmapować napotka międzyoperacyjnego organizatora.</span><span class="sxs-lookup"><span data-stu-id="487cb-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="487cb-123">Zastrzeżone</span><span class="sxs-lookup"><span data-stu-id="487cb-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="487cb-124">Zezwalaj na wywoływany do wywołania Win32 `SetLastError` funkcja przed powrotem z metody oparte na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="487cb-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="487cb-125">Zastrzeżone</span><span class="sxs-lookup"><span data-stu-id="487cb-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="487cb-126">Za pomocą platformy domyślnej konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="487cb-126">Use the default platform calling convention.</span></span> <span data-ttu-id="487cb-127">Na przykład w systemie Windows wartość domyślna to `StdCall` i na Windows CE .NET jest `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="487cb-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="487cb-128">Użyj `Cdecl` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="487cb-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="487cb-129">W takim przypadku obiekt wywołujący czyści stosu.</span><span class="sxs-lookup"><span data-stu-id="487cb-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="487cb-130">Dzięki temu wywoływanie funkcji z `varargs` (to znaczy, funkcje, które zaakceptować zmienną liczbę parametrów).</span><span class="sxs-lookup"><span data-stu-id="487cb-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="487cb-131">Użyj `StdCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="487cb-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="487cb-132">W takim przypadku wywoływany czyści stosu.</span><span class="sxs-lookup"><span data-stu-id="487cb-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="487cb-133">Jest domyślnej konwencji wywołania wywoływanie niezarządzanych funkcji z platformą.</span><span class="sxs-lookup"><span data-stu-id="487cb-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="487cb-134">Użyj `ThisCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="487cb-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="487cb-135">W tym przypadku jest pierwszym parametrem `this` wskaźnik i są przechowywane w rejestrze ECX.</span><span class="sxs-lookup"><span data-stu-id="487cb-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="487cb-136">Inne parametry są przenoszone na stosie.</span><span class="sxs-lookup"><span data-stu-id="487cb-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="487cb-137">`ThisCall` Konwencji wywoływania są używane do wywoływania metod w klasach wyeksportowane z niezarządzanej DLL.</span><span class="sxs-lookup"><span data-stu-id="487cb-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="487cb-138">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="487cb-139">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="487cb-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="487cb-140">Wymagania</span><span class="sxs-lookup"><span data-stu-id="487cb-140">Requirements</span></span>  
 <span data-ttu-id="487cb-141">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="487cb-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="487cb-142">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="487cb-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="487cb-143">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="487cb-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="487cb-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="487cb-144">See Also</span></span>  
 [<span data-ttu-id="487cb-145">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="487cb-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
