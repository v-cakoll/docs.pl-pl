---
title: "IAssemblyCache::InstallAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.InstallAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1207c2dc5b29b8de084ccb9145e886f34e8144b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="523bf-102">IAssemblyCache::InstallAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="523bf-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="523bf-103">Instaluje określonego zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="523bf-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523bf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="523bf-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="523bf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="523bf-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="523bf-106">[in] Flagi zdefiniowane w Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="523bf-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="523bf-107">Obsługiwane są następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="523bf-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="523bf-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="523bf-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="523bf-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="523bf-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="523bf-110">[in] Ścieżka do manifestu zestawu do instalacji.</span><span class="sxs-lookup"><span data-stu-id="523bf-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="523bf-111">[in] A [fusion_install_reference —](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) struktury, która zawiera dane dotyczące instalacji.</span><span class="sxs-lookup"><span data-stu-id="523bf-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523bf-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="523bf-112">Requirements</span></span>  
 <span data-ttu-id="523bf-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="523bf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523bf-114">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="523bf-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="523bf-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523bf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523bf-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="523bf-116">See Also</span></span>  
 [<span data-ttu-id="523bf-117">IAssemblyCache — interfejs</span><span class="sxs-lookup"><span data-stu-id="523bf-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
