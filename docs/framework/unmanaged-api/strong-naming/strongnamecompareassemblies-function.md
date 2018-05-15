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
ms.openlocfilehash: 4bd1d098f21a3d5ba43b6251c87c36df4347a924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="e0a2a-102">StrongNameCompareAssemblies — Funkcja</span><span class="sxs-lookup"><span data-stu-id="e0a2a-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="e0a2a-103">Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="e0a2a-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-104">This function has been deprecated.</span></span> <span data-ttu-id="e0a2a-105">Użyj [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a2a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0a2a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e0a2a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a2a-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="e0a2a-108">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="e0a2a-109">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="e0a2a-110">[out] Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="e0a2a-110">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="e0a2a-111">`SN_CMP_DIFFERENT` (0) — określa, czy zestawy zawierać innych danych.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="e0a2a-112">`SN_CMP_IDENTICAL` (1) — określa, czy zestawy są dokładnie takie same, w tym ich podpisów i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="e0a2a-113">`SN_CMP_SIGONLY` (2) — określa, czy zestawy różnią się jedynie podpisu i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a2a-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0a2a-114">Return Value</span></span>  
 <span data-ttu-id="e0a2a-115">`true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0a2a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0a2a-116">Requirements</span></span>  
 <span data-ttu-id="e0a2a-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a2a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a2a-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e0a2a-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e0a2a-119">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0a2a-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e0a2a-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0a2a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0a2a-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0a2a-121">Remarks</span></span>  
 <span data-ttu-id="e0a2a-122">Podpis silnej nazwy zestawu składa się z zestawu tekst nazwę, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="e0a2a-123">Jeśli `StrongNameCompareAssemblies` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.</span><span class="sxs-lookup"><span data-stu-id="e0a2a-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a2a-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0a2a-124">See Also</span></span>  
 [<span data-ttu-id="e0a2a-125">StrongNameCompareAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="e0a2a-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)  
 [<span data-ttu-id="e0a2a-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a2a-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
