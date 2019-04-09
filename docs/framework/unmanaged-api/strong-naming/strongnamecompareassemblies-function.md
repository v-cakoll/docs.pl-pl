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
ms.openlocfilehash: 2a49252d00f75b4d0b6325aeae0aab22f8ada5e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191383"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="3961c-102">StrongNameCompareAssemblies — Funkcja</span><span class="sxs-lookup"><span data-stu-id="3961c-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="3961c-103">Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3961c-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="3961c-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="3961c-104">This function has been deprecated.</span></span> <span data-ttu-id="3961c-105">Użyj [iclrstrongname::strongnamecompareassemblies —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3961c-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3961c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="3961c-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3961c-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3961c-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="3961c-108">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3961c-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="3961c-109">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3961c-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="3961c-110">[out] Jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="3961c-110">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="3961c-111">(0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="3961c-111">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="3961c-112">(1) — określa, że zestawy są dokładnie takie same, łącznie z ich podpisy i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="3961c-112">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="3961c-113">(2) — określa, że zestawy różnią się jedynie podpisu i sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="3961c-113">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3961c-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3961c-114">Return Value</span></span>  
 `true` <span data-ttu-id="3961c-115">Po pomyślnym zakończeniu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="3961c-115">on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3961c-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3961c-116">Requirements</span></span>  
 <span data-ttu-id="3961c-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3961c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3961c-118">**Nagłówek:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="3961c-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3961c-119">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3961c-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="3961c-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3961c-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="3961c-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3961c-121">Remarks</span></span>  
 <span data-ttu-id="3961c-122">Podpis silnej nazwy zestawu składa się z tekstu nazwę zestawu, wersji, kultury i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="3961c-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="3961c-123">Jeśli `StrongNameCompareAssemblies` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="3961c-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3961c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3961c-124">See also</span></span>

- [<span data-ttu-id="3961c-125">StrongNameCompareAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="3961c-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="3961c-126">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3961c-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
