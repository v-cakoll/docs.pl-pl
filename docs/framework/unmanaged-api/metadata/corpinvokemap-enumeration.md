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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079633"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="eb209-102">CorPinvokeMap — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eb209-102">CorPinvokeMap Enumeration</span></span>
<span data-ttu-id="eb209-103">Określa opcje dla wywołań PInvoke.</span><span class="sxs-lookup"><span data-stu-id="eb209-103">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb209-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb209-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="eb209-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eb209-105">Members</span></span>  
  
|<span data-ttu-id="eb209-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="eb209-106">Member</span></span>|<span data-ttu-id="eb209-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eb209-107">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="eb209-108">Użyj nazwy elementów członkowskich określonych.</span><span class="sxs-lookup"><span data-stu-id="eb209-108">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="eb209-109">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-109">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="eb209-110">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-110">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="eb209-111">Przeprowadzanie marshalingu ciągów jako ciągi wielu-bajtowych wartości znakowych.</span><span class="sxs-lookup"><span data-stu-id="eb209-111">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="eb209-112">Przeprowadzanie marshalingu ciągów Unicode znaki 2-bajtowe.</span><span class="sxs-lookup"><span data-stu-id="eb209-112">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="eb209-113">Automatycznie kierować ciągi, odpowiednio dla docelowego systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="eb209-113">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="eb209-114">Wartość domyślna to Unicode na Windows NT, Windows 2000, Windows XP i rodziny Windows Server 2003; Wartość domyślna to ANSI w systemach Windows 98 i Windows Me.</span><span class="sxs-lookup"><span data-stu-id="eb209-114">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="eb209-115">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-115">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="eb209-116">Wykonaj mapowanie znaków Unicode, których brakuje dokładnego dopasowania do zestawu znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="eb209-116">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="eb209-117">Nie wykonuj mapowanie znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="eb209-117">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="eb209-118">W takim przypadku wszystkie, którego nie można zmapować znaki zostaną zastąpione przez "?".</span><span class="sxs-lookup"><span data-stu-id="eb209-118">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="eb209-119">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-119">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="eb209-120">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="eb209-121">Zgłoś wyjątek, jeśli Organizator międzyoperacyjny napotka znaku, którego nie można zmapować.</span><span class="sxs-lookup"><span data-stu-id="eb209-121">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="eb209-122">Nie zgłasza wyjątku, gdy organizator międzyoperacyjny napotka znaku, którego nie można zmapować.</span><span class="sxs-lookup"><span data-stu-id="eb209-122">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="eb209-123">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="eb209-123">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="eb209-124">Zezwalaj na / / wywoływany w celu wywołania Win32 `SetLastError` funkcji przed zwróceniem z atrybutami metody.</span><span class="sxs-lookup"><span data-stu-id="eb209-124">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="eb209-125">Zarezerwowany</span><span class="sxs-lookup"><span data-stu-id="eb209-125">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="eb209-126">Użyj platformy domyślną konwencję wywoływania.</span><span class="sxs-lookup"><span data-stu-id="eb209-126">Use the default platform calling convention.</span></span> <span data-ttu-id="eb209-127">Na przykład na Windows wartość domyślna to `StdCall` i na Windows CE .NET jest `Cdecl`.</span><span class="sxs-lookup"><span data-stu-id="eb209-127">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="eb209-128">Użyj `Cdecl` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="eb209-128">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="eb209-129">W tym przypadku obiekt wywołujący czyści stos.</span><span class="sxs-lookup"><span data-stu-id="eb209-129">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="eb209-130">Dzięki temu wywoływania funkcji z `varargs` (oznacza to, funkcje, które przyjmują zmienną liczbę parametrów).</span><span class="sxs-lookup"><span data-stu-id="eb209-130">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="eb209-131">Użyj `StdCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="eb209-131">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="eb209-132">W tym przypadku wywoływany obiekt czyści stos.</span><span class="sxs-lookup"><span data-stu-id="eb209-132">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="eb209-133">To jest domyślna konwencja wywoływania niezarządzanych przy użyciu platformy wywołają procedurę obsługi.</span><span class="sxs-lookup"><span data-stu-id="eb209-133">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="eb209-134">Użyj `ThisCall` konwencji wywoływania.</span><span class="sxs-lookup"><span data-stu-id="eb209-134">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="eb209-135">W tym przypadku jest pierwszym parametrem `this` wskaźnika i jest przechowywany w rejestrze ECX.</span><span class="sxs-lookup"><span data-stu-id="eb209-135">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="eb209-136">Inne parametry są przekazywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="eb209-136">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="eb209-137">`ThisCall` Konwencji wywoływania służy do wywoływania metod w klasach wyeksportowane z niezarządzaną biblioteką DLL.</span><span class="sxs-lookup"><span data-stu-id="eb209-137">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="eb209-138">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-138">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="eb209-139">Zastrzeżone.</span><span class="sxs-lookup"><span data-stu-id="eb209-139">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eb209-140">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb209-140">Requirements</span></span>  
 <span data-ttu-id="eb209-141">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb209-141">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb209-142">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="eb209-142">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="eb209-143">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb209-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb209-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb209-144">See also</span></span>

- [<span data-ttu-id="eb209-145">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="eb209-145">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
