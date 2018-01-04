---
title: "IMetaDataDispenserEx::FindAssemblyModule — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 482bc9b9a89d876e7ac09fcb4edcd190adc168f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="5c299-102">IMetaDataDispenserEx::FindAssemblyModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="5c299-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="5c299-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="5c299-103">This method is not implemented.</span></span> <span data-ttu-id="5c299-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="5c299-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c299-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c299-105">Syntax</span></span>  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c299-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5c299-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="5c299-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5c299-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="5c299-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5c299-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="5c299-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="5c299-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="5c299-110">[in] Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="5c299-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="5c299-111">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="5c299-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="5c299-112">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="5c299-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5c299-113">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="5c299-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="5c299-114">[out] Liczba znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="5c299-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c299-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c299-115">Requirements</span></span>  
 <span data-ttu-id="5c299-116">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c299-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c299-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5c299-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c299-118">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5c299-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5c299-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c299-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c299-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c299-120">See Also</span></span>  
 [<span data-ttu-id="5c299-121">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c299-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="5c299-122">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="5c299-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
