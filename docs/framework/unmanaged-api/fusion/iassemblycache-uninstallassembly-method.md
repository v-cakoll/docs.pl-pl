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
ms.openlocfilehash: 63c1cb3c417e8e521c6ac8417d260ccb937863f8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796745"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="e8ff2-102">IAssemblyCache::UninstallAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8ff2-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="e8ff2-103">Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="e8ff2-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ff2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ff2-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8ff2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8ff2-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="e8ff2-106">podczas Flagi zdefiniowane w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="e8ff2-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="e8ff2-107">podczas Nazwa zestawu do odinstalowania.</span><span class="sxs-lookup"><span data-stu-id="e8ff2-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="e8ff2-108">podczas Struktura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) , która zawiera dane instalacji dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="e8ff2-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="e8ff2-109">[out, opcjonalne] Jedna z wartości dyspozycji zdefiniowanych w pliku Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="e8ff2-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="e8ff2-110">Możliwe wartości:</span><span class="sxs-lookup"><span data-stu-id="e8ff2-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="e8ff2-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="e8ff2-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="e8ff2-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="e8ff2-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="e8ff2-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="e8ff2-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="e8ff2-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8ff2-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ff2-117">Requirements</span></span>  
 <span data-ttu-id="e8ff2-118">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ff2-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ff2-119">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="e8ff2-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e8ff2-120">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ff2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ff2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8ff2-121">See also</span></span>

- [<span data-ttu-id="e8ff2-122">IAssemblyCache, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8ff2-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
