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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176152"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="b6e43-102">CorPinvokeMap — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b6e43-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="b6e43-103">Określa opcje wywołania PInvoke.</span><span class="sxs-lookup"><span data-stu-id="b6e43-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6e43-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b6e43-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b6e43-105">Members</span></span>  
  
|<span data-ttu-id="b6e43-106">Członek</span><span class="sxs-lookup"><span data-stu-id="b6e43-106">Member</span></span>|<span data-ttu-id="b6e43-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6e43-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="b6e43-108">Użyj każdej nazwy elementu członkowskiego, jak określono.</span><span class="sxs-lookup"><span data-stu-id="b6e43-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="b6e43-109">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="b6e43-110">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="b6e43-111">Ciągi marshal jako ciągi znaków wielo bajtów.</span><span class="sxs-lookup"><span data-stu-id="b6e43-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="b6e43-112">Ciągi marshaljako 2-bajtowe znaki Unicode.</span><span class="sxs-lookup"><span data-stu-id="b6e43-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="b6e43-113">Automatycznie marshal ciągi odpowiednio dla docelowego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b6e43-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="b6e43-114">Domyślnie jest to Unicode w systemach Windows NT, Windows 2000, Windows XP i Windows Server 2003; domyślnie jest ANSI w systemie Windows 98 i Windows Me.</span><span class="sxs-lookup"><span data-stu-id="b6e43-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="b6e43-115">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="b6e43-116">Wykonaj najlepsze mapowanie znaków Unicode, które nie mają dokładnego dopasowania w zestawie znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="b6e43-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="b6e43-117">Nie należy wykonywać najkosztowanego mapowania znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="b6e43-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="b6e43-118">W takim przypadku wszystkie znaki, które nie można zastosować, zostaną zastąpione przez '?'.</span><span class="sxs-lookup"><span data-stu-id="b6e43-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="b6e43-119">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="b6e43-120">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="b6e43-121">Zgłosić wyjątek, gdy organizator międzyoperacyjny napotka znak niezadający do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b6e43-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="b6e43-122">Nie zgłaszaj wyjątku, gdy organizator międzyoperacyjny napotka znak niemożna zastosować.</span><span class="sxs-lookup"><span data-stu-id="b6e43-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="b6e43-123">Zarezerwowano</span><span class="sxs-lookup"><span data-stu-id="b6e43-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="b6e43-124">Zezwalaj wywołującemu na wywołanie `SetLastError` funkcji Win32 przed zwróceniem z przypisanej metody.</span><span class="sxs-lookup"><span data-stu-id="b6e43-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="b6e43-125">Zarezerwowano</span><span class="sxs-lookup"><span data-stu-id="b6e43-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="b6e43-126">Użyj domyślnej konwencji wywoływania platformy.</span><span class="sxs-lookup"><span data-stu-id="b6e43-126">Use the default platform calling convention.</span></span> <span data-ttu-id="b6e43-127">Na przykład w systemie `StdCall` Windows domyślny jest i `Cdecl`w systemie Windows CE .NET jest .</span><span class="sxs-lookup"><span data-stu-id="b6e43-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="b6e43-128">Użyj `Cdecl` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="b6e43-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="b6e43-129">W takim przypadku obiektu wywołującego czyści stosu.</span><span class="sxs-lookup"><span data-stu-id="b6e43-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="b6e43-130">Umożliwia to wywoływanie funkcji z `varargs` (czyli funkcje, które akceptują zmienną liczbę parametrów).</span><span class="sxs-lookup"><span data-stu-id="b6e43-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="b6e43-131">Użyj `StdCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="b6e43-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="b6e43-132">W takim przypadku wywoływany czyści stosu.</span><span class="sxs-lookup"><span data-stu-id="b6e43-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="b6e43-133">Jest to domyślna konwencja wywoływania niezarządzanych funkcji za pomocą wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="b6e43-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="b6e43-134">Użyj `ThisCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="b6e43-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="b6e43-135">W takim przypadku pierwszym parametrem `this` jest wskaźnik i jest przechowywany w rejestrze ECX.</span><span class="sxs-lookup"><span data-stu-id="b6e43-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="b6e43-136">Inne parametry są wypychane na stosie.</span><span class="sxs-lookup"><span data-stu-id="b6e43-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="b6e43-137">Konwencja wywołująca `ThisCall` jest używana do wywoływania metod na klasy eksportowane z biblioteki DLL niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="b6e43-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="b6e43-138">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="b6e43-139">Zarezerwowany.</span><span class="sxs-lookup"><span data-stu-id="b6e43-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6e43-140">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6e43-140">Requirements</span></span>  
 <span data-ttu-id="b6e43-141">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6e43-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e43-142">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b6e43-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b6e43-143">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e43-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e43-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6e43-144">See also</span></span>

- [<span data-ttu-id="b6e43-145">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b6e43-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
