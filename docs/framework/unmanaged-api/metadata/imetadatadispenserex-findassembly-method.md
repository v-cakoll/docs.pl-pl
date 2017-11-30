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
ms.openlocfilehash: 7a70d1e2b3636a405fe28b84c2e76dd7264df4f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="c51b2-102">IMetaDataDispenserEx::FindAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="c51b2-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="c51b2-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="c51b2-103">This method is not implemented.</span></span> <span data-ttu-id="c51b2-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="c51b2-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c51b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c51b2-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="c51b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c51b2-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="c51b2-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c51b2-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="c51b2-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c51b2-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="c51b2-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c51b2-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="c51b2-110">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="c51b2-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="c51b2-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="c51b2-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="c51b2-112">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="c51b2-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="c51b2-113">[out] Liczba znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="c51b2-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c51b2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c51b2-114">Requirements</span></span>  
 <span data-ttu-id="c51b2-115">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c51b2-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c51b2-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c51b2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c51b2-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c51b2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c51b2-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c51b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c51b2-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c51b2-119">See Also</span></span>  
 [<span data-ttu-id="c51b2-120">IMetaDataDispenserEx — interfejs</span><span class="sxs-lookup"><span data-stu-id="c51b2-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="c51b2-121">IMetaDataDispenser — interfejs</span><span class="sxs-lookup"><span data-stu-id="c51b2-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
