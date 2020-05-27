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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007549"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="ef378-102">CorPinvokeMap — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ef378-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="ef378-103">Określa opcje wywołania PInvoke.</span><span class="sxs-lookup"><span data-stu-id="ef378-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef378-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef378-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ef378-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ef378-105">Members</span></span>  
  
|<span data-ttu-id="ef378-106">Członek</span><span class="sxs-lookup"><span data-stu-id="ef378-106">Member</span></span>|<span data-ttu-id="ef378-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ef378-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="ef378-108">Użyj każdej nazwy elementu członkowskiego w określony sposób.</span><span class="sxs-lookup"><span data-stu-id="ef378-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="ef378-109">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="ef378-110">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="ef378-111">Kierowanie ciągów jako ciągów znaków wielobajtowych.</span><span class="sxs-lookup"><span data-stu-id="ef378-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="ef378-112">Kierowanie ciągów jako znaków Unicode 2-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="ef378-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="ef378-113">Automatyczne kierowanie ciągów odpowiednio dla docelowego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ef378-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="ef378-114">Wartość domyślna to Unicode w systemie Windows NT, Windows 2000, Windows XP i rodziny Windows Server 2003. wartość domyślna to ANSI w systemach Windows 98 i Windows Me.</span><span class="sxs-lookup"><span data-stu-id="ef378-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="ef378-115">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="ef378-116">Wykonaj najlepiej dopasowane mapowanie znaków Unicode, które nie mają dokładnego dopasowania w zestawie znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="ef378-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="ef378-117">Nie wykonuj najlepszego mapowania znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef378-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="ef378-118">W takim przypadku wszystkie znaki napotkano zostaną zastąpione "?".</span><span class="sxs-lookup"><span data-stu-id="ef378-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="ef378-119">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="ef378-120">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="ef378-121">Zgłoś wyjątek, gdy organizator międzyoperacyjny napotka znak napotkano.</span><span class="sxs-lookup"><span data-stu-id="ef378-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="ef378-122">Nie zgłaszaj wyjątku, gdy organizator międzyoperacyjny napotka znak napotkano.</span><span class="sxs-lookup"><span data-stu-id="ef378-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="ef378-123">Zarezerwowano</span><span class="sxs-lookup"><span data-stu-id="ef378-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="ef378-124">Zezwalaj wywołującemu na wywoływanie `SetLastError` funkcji Win32 przed powrotem z metody z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="ef378-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="ef378-125">Zarezerwowano</span><span class="sxs-lookup"><span data-stu-id="ef378-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="ef378-126">Użyj domyślnej konwencji wywoływania platformy.</span><span class="sxs-lookup"><span data-stu-id="ef378-126">Use the default platform calling convention.</span></span> <span data-ttu-id="ef378-127">Na przykład w systemie Windows jest to ustawienie domyślne `StdCall` i na Windows CE .NET `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="ef378-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="ef378-128">Użyj `Cdecl` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="ef378-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="ef378-129">W takim przypadku wywołujący czyści stos.</span><span class="sxs-lookup"><span data-stu-id="ef378-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="ef378-130">Umożliwia to wywoływanie funkcji za pomocą `varargs` (czyli funkcji, które akceptują zmienną liczbę parametrów).</span><span class="sxs-lookup"><span data-stu-id="ef378-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="ef378-131">Użyj `StdCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="ef378-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="ef378-132">W takim przypadku wywoływany czyści stos.</span><span class="sxs-lookup"><span data-stu-id="ef378-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="ef378-133">Jest to domyślna konwencja wywoływania funkcji niezarządzanych przy użyciu wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="ef378-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="ef378-134">Użyj `ThisCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="ef378-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="ef378-135">W tym przypadku pierwszy parametr jest `this` wskaźnikiem i jest przechowywany w rejestrze ECX.</span><span class="sxs-lookup"><span data-stu-id="ef378-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="ef378-136">Inne parametry są wypychane na stosie.</span><span class="sxs-lookup"><span data-stu-id="ef378-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="ef378-137">`ThisCall`Konwencja wywoływania jest używana do wywoływania metod w klasach wyeksportowanych z niezarządzanej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="ef378-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="ef378-138">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="ef378-139">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="ef378-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ef378-140">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef378-140">Requirements</span></span>  
 <span data-ttu-id="ef378-141">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef378-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef378-142">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ef378-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ef378-143">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef378-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef378-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef378-144">See also</span></span>

- [<span data-ttu-id="ef378-145">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ef378-145">Metadata Enumerations</span></span>](metadata-enumerations.md)
