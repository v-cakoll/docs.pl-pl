---
title: ICLRStrongName::StrongNameCompareAssemblies — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cdc59228ff9913be808d3909ca3fe9e38a7c72f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584320"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="fdb06-102">ICLRStrongName::StrongNameCompareAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdb06-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="fdb06-103">Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="fdb06-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdb06-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdb06-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="fdb06-106">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fdb06-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="fdb06-107">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="fdb06-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="fdb06-108">[out] Jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="fdb06-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="fdb06-109">`SN_CMP_DIFFERENT` (0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="fdb06-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="fdb06-110">`SN_CMP_IDENTICAL` (1) — określa, że zestawy są dokładnie takie same, łącznie z ich podpisy i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="fdb06-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="fdb06-111">`SN_CMP_SIGONLY` (2) — określa, że zestawy różnią się jedynie podpisu i sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="fdb06-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdb06-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fdb06-112">Return Value</span></span>  
 <span data-ttu-id="fdb06-113">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="fdb06-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb06-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdb06-114">Requirements</span></span>  
 <span data-ttu-id="fdb06-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdb06-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb06-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fdb06-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fdb06-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdb06-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdb06-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb06-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdb06-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdb06-119">Remarks</span></span>  
 <span data-ttu-id="fdb06-120">Podpis silnej nazwy zestawu składa się z tekstu nazwę zestawu, wersji, kultury i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="fdb06-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb06-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdb06-121">See also</span></span>

- [<span data-ttu-id="fdb06-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdb06-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
