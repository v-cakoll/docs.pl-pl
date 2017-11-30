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
ms.openlocfilehash: 3911eeb5f6ff8122c71f0c1df973c4636ad8b665
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="28cf5-102">IMetaDataDispenserEx::FindAssemblyModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="28cf5-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="28cf5-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="28cf5-103">This method is not implemented.</span></span> <span data-ttu-id="28cf5-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="28cf5-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28cf5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="28cf5-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="28cf5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="28cf5-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="28cf5-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="28cf5-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="28cf5-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="28cf5-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="28cf5-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="28cf5-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="28cf5-110">[in] Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="28cf5-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="28cf5-111">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="28cf5-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="28cf5-112">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="28cf5-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="28cf5-113">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="28cf5-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="28cf5-114">[out] Liczba znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="28cf5-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28cf5-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28cf5-115">Requirements</span></span>  
 <span data-ttu-id="28cf5-116">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28cf5-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28cf5-117">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="28cf5-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="28cf5-118">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="28cf5-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28cf5-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28cf5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cf5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28cf5-120">See Also</span></span>  
 [<span data-ttu-id="28cf5-121">IMetaDataDispenserEx — interfejs</span><span class="sxs-lookup"><span data-stu-id="28cf5-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="28cf5-122">IMetaDataDispenser — interfejs</span><span class="sxs-lookup"><span data-stu-id="28cf5-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
