---
title: IAssemblyCache::UninstallAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6be40ecbb801348ad73fb929741b5a8e8407a7ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428435"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="ebfb2-102">IAssemblyCache::UninstallAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="ebfb2-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="ebfb2-103">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="ebfb2-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebfb2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebfb2-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ebfb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ebfb2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="ebfb2-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="ebfb2-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="ebfb2-107">[in] Nazwa zestawu do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="ebfb2-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="ebfb2-108">[in] A [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktury, która zawiera dane instalacji dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="ebfb2-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="ebfb2-109">[out, opcjonalnie] Jedna z wartości dyspozycji zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="ebfb2-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="ebfb2-110">Możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="ebfb2-110">Possible values include the following:</span></span>  
  
-   <span data-ttu-id="ebfb2-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
-   <span data-ttu-id="ebfb2-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
-   <span data-ttu-id="ebfb2-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
-   <span data-ttu-id="ebfb2-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
-   <span data-ttu-id="ebfb2-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
-   <span data-ttu-id="ebfb2-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="ebfb2-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebfb2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebfb2-117">Requirements</span></span>  
 <span data-ttu-id="ebfb2-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebfb2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebfb2-119">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ebfb2-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ebfb2-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebfb2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebfb2-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebfb2-121">See Also</span></span>  
 [<span data-ttu-id="ebfb2-122">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebfb2-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
