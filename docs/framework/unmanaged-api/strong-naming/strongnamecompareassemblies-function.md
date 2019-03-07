---
title: StrongNameCompareAssemblies — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd3813d977f94db4168da8c888485b323f4072ad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471280"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="ac407-102">StrongNameCompareAssemblies — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ac407-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="ac407-103">Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="ac407-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="ac407-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="ac407-104">This function has been deprecated.</span></span> <span data-ttu-id="ac407-105">Użyj [iclrstrongname::strongnamecompareassemblies —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ac407-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac407-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac407-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac407-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac407-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="ac407-108">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac407-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="ac407-109">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac407-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="ac407-110">[out] Jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="ac407-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="ac407-111">`SN_CMP_DIFFERENT` (0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="ac407-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="ac407-112">`SN_CMP_IDENTICAL` (1) — określa, że zestawy są dokładnie takie same, łącznie z ich podpisy i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="ac407-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="ac407-113">`SN_CMP_SIGONLY` (2) — określa, że zestawy różnią się jedynie podpisu i sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="ac407-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ac407-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ac407-114">Return Value</span></span>  
 <span data-ttu-id="ac407-115">`true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="ac407-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac407-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac407-116">Requirements</span></span>  
 <span data-ttu-id="ac407-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac407-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac407-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ac407-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ac407-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac407-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac407-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac407-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac407-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac407-121">Remarks</span></span>  
 <span data-ttu-id="ac407-122">Podpis silnej nazwy zestawu składa się z tekstu nazwę zestawu, wersji, kultury i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ac407-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="ac407-123">Jeśli `StrongNameCompareAssemblies` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="ac407-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac407-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac407-124">See also</span></span>
- [<span data-ttu-id="ac407-125">StrongNameCompareAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="ac407-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="ac407-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac407-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
