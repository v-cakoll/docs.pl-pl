---
title: "ICLRStrongName::StrongNameCompareAssemblies — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameCompareAssemblies
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96fbeccf76de87a3582bf8c2084d0ca9ad7d27f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="77706-102">ICLRStrongName::StrongNameCompareAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="77706-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="77706-103">Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="77706-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77706-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="77706-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77706-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="77706-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="77706-106">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="77706-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="77706-107">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="77706-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="77706-108">[out] Jedna z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="77706-108">[out] One of the following values:</span></span>  
  
-   <span data-ttu-id="77706-109">`SN_CMP_DIFFERENT`(0) — określa, czy zestawy zawierać innych danych.</span><span class="sxs-lookup"><span data-stu-id="77706-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
-   <span data-ttu-id="77706-110">`SN_CMP_IDENTICAL`(1) — określa, czy zestawy są dokładnie takie same, w tym ich podpisów i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="77706-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   <span data-ttu-id="77706-111">`SN_CMP_SIGONLY`(2) — określa, czy zestawy różnią się jedynie podpisu i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="77706-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77706-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="77706-112">Return Value</span></span>  
 <span data-ttu-id="77706-113">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="77706-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77706-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="77706-114">Requirements</span></span>  
 <span data-ttu-id="77706-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77706-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77706-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="77706-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="77706-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77706-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77706-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77706-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77706-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="77706-119">Remarks</span></span>  
 <span data-ttu-id="77706-120">Podpis silnej nazwy zestawu składa się z zestawu tekst nazwę, wersję, kulturę i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="77706-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77706-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77706-121">See Also</span></span>  
 [<span data-ttu-id="77706-122">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="77706-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
