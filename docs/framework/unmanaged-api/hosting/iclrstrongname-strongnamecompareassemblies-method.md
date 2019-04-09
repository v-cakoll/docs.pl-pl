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
ms.openlocfilehash: 63d4b885b6968b800bc965a9be1ec6b795a42220
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140663"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="92c8b-102">ICLRStrongName::StrongNameCompareAssemblies — Metoda</span><span class="sxs-lookup"><span data-stu-id="92c8b-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="92c8b-103">Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="92c8b-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c8b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92c8b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c8b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92c8b-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="92c8b-106">[in] Ścieżka do pierwszego zestawu.</span><span class="sxs-lookup"><span data-stu-id="92c8b-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="92c8b-107">[in] Ścieżka do drugiego zestawu.</span><span class="sxs-lookup"><span data-stu-id="92c8b-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="92c8b-108">[out] Jeden z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="92c8b-108">[out] One of the following values:</span></span>  
  
-   `SN_CMP_DIFFERENT` <span data-ttu-id="92c8b-109">(0) — określa, że zestawy zawierają różne dane.</span><span class="sxs-lookup"><span data-stu-id="92c8b-109">(0) - Specifies that the assemblies contain different data.</span></span>  
  
-   `SN_CMP_IDENTICAL` <span data-ttu-id="92c8b-110">(1) — określa, że zestawy są dokładnie takie same, łącznie z ich podpisy i sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="92c8b-110">(1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
-   `SN_CMP_SIGONLY` <span data-ttu-id="92c8b-111">(2) — określa, że zestawy różnią się jedynie podpisu i sum kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="92c8b-111">(2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92c8b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="92c8b-112">Return Value</span></span>  
 `S_OK` <span data-ttu-id="92c8b-113">Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="92c8b-113">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c8b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92c8b-114">Requirements</span></span>  
 <span data-ttu-id="92c8b-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c8b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c8b-116">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="92c8b-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="92c8b-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92c8b-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="92c8b-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="92c8b-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a><span data-ttu-id="92c8b-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92c8b-119">Remarks</span></span>  
 <span data-ttu-id="92c8b-120">Podpis silnej nazwy zestawu składa się z tekstu nazwę zestawu, wersji, kultury i token klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="92c8b-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c8b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92c8b-121">See also</span></span>

- [<span data-ttu-id="92c8b-122">ICLRStrongName — Interfejs</span><span class="sxs-lookup"><span data-stu-id="92c8b-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
