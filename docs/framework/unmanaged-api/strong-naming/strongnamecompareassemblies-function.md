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
ms.openlocfilehash: b0c2e8e46c7bb3a5e693c9ea16e6c5a0722b1898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799154"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="a3fb3-102">StrongNameCompareAssemblies — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a3fb3-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="a3fb3-103">Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="a3fb3-104">Ta funkcja jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-104">This function has been deprecated.</span></span> <span data-ttu-id="a3fb3-105">Zamiast tego użyj metody [ICLRStrongName:: StrongNameCompareAssemblies —](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a3fb3-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fb3-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a3fb3-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3fb3-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a3fb3-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="a3fb3-108">podczas Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="a3fb3-109">podczas Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="a3fb3-110">określoną Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="a3fb3-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="a3fb3-111">`SN_CMP_DIFFERENT`(0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="a3fb3-112">`SN_CMP_IDENTICAL`(1) — określa, że zestawy są dokładnie takie same, łącznie z ich sygnaturami i sumą kontrolną.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="a3fb3-113">`SN_CMP_SIGONLY`(2) — określa, że zestawy różnią się tylko sygnaturą i sumą kontrolną.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3fb3-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a3fb3-114">Return Value</span></span>  
 <span data-ttu-id="a3fb3-115">`true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`</span><span class="sxs-lookup"><span data-stu-id="a3fb3-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3fb3-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3fb3-116">Requirements</span></span>  
 <span data-ttu-id="a3fb3-117">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb3-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fb3-118">**Nagłówki** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="a3fb3-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a3fb3-119">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3fb3-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a3fb3-120">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3fb3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3fb3-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3fb3-121">Remarks</span></span>  
 <span data-ttu-id="a3fb3-122">Podpis silnej nazwy zestawu składa się z nazwy tekstu, wersji, kultury i tokenu klucza publicznego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="a3fb3-123">Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameCompareAssemblies`</span><span class="sxs-lookup"><span data-stu-id="a3fb3-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fb3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3fb3-124">See also</span></span>

- [<span data-ttu-id="a3fb3-125">StrongNameCompareAssemblies, metoda</span><span class="sxs-lookup"><span data-stu-id="a3fb3-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="a3fb3-126">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3fb3-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
