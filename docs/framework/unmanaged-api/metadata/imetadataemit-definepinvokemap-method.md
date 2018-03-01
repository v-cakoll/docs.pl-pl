---
title: "IMetaDataEmit::DefinePinvokeMap — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bd42c54990fd8aad1b9e6325d59ac7ccc5d6a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="abc54-102">IMetaDataEmit::DefinePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="abc54-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="abc54-103">Ustawia funkcje metody odwołuje się określony token podpisu funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="abc54-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abc54-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abc54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abc54-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="abc54-106">[in] Token metody docelowej.</span><span class="sxs-lookup"><span data-stu-id="abc54-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="abc54-107">[in] Flagi używane przez funkcji PInvoke w celu mapowania.</span><span class="sxs-lookup"><span data-stu-id="abc54-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="abc54-108">[in] Nazwa elementu docelowego eksportu metody w bibliotece DLL niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="abc54-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="abc54-109">[in] Token dla obiekt docelowy natywnej biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="abc54-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc54-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abc54-110">Requirements</span></span>  
 <span data-ttu-id="abc54-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abc54-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abc54-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abc54-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abc54-113">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abc54-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abc54-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abc54-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc54-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abc54-115">See Also</span></span>  
 [<span data-ttu-id="abc54-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="abc54-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="abc54-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="abc54-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
