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
ms.openlocfilehash: c5020c31f590f527856f966ede512e98c07496ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435391"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="0fd8f-102">ICLRStrongName::StrongNameCompareAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="0fd8f-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="0fd8f-103">Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fd8f-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fd8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0fd8f-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="0fd8f-106">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="0fd8f-107">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="0fd8f-108">[out] Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="0fd8f-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="0fd8f-109">`SN_CMP_DIFFERENT` (0) — określa, czy zestawy zawierać innych danych.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="0fd8f-110">`SN_CMP_IDENTICAL` (1) — określa, czy zestawy są dokładnie takie same, w tym ich podpisów i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="0fd8f-111">`SN_CMP_SIGONLY` (2) — określa, czy zestawy różnią się jedynie podpisu i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0fd8f-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0fd8f-112">Return Value</span></span>  
 <span data-ttu-id="0fd8f-113">`S_OK` Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="0fd8f-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd8f-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fd8f-114">Requirements</span></span>  
 <span data-ttu-id="0fd8f-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fd8f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd8f-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0fd8f-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0fd8f-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0fd8f-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fd8f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd8f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fd8f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fd8f-119">Remarks</span></span>  
 <span data-ttu-id="0fd8f-120">Podpis silnej nazwy zestawu składa się z zestawu tekst nazwę, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="0fd8f-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd8f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fd8f-121">See Also</span></span>  
 [<span data-ttu-id="0fd8f-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="0fd8f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
