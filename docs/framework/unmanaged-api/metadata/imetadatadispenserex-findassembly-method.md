---
title: "IMetaDataDispenserEx::FindAssembly — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f125008e4ae5b7f2abbe6d467b486b962700d42
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c0652-102">IMetaDataDispenserEx::FindAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="c0652-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c0652-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="c0652-103">This method is not implemented.</span></span> <span data-ttu-id="c0652-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c0652-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0652-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c0652-105">Syntax</span></span>  
  
```  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0652-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c0652-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c0652-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c0652-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c0652-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c0652-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c0652-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c0652-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c0652-110">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="c0652-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0652-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="c0652-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c0652-112">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="c0652-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c0652-113">[out] Liczba znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="c0652-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0652-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c0652-114">Requirements</span></span>  
 <span data-ttu-id="c0652-115">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0652-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0652-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c0652-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c0652-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0652-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0652-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0652-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0652-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0652-119">See Also</span></span>  
 [<span data-ttu-id="c0652-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0652-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="c0652-121">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="c0652-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
