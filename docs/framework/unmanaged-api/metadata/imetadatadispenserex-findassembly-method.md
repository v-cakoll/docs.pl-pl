---
title: IMetaDataDispenserEx::FindAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b4caf27fe45ce0a85b7e1800827a1e5cd0893ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445241"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="de480-102">IMetaDataDispenserEx::FindAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="de480-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="de480-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="de480-103">This method is not implemented.</span></span> <span data-ttu-id="de480-104">Wywołuje się, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="de480-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de480-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="de480-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="de480-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="de480-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="de480-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="de480-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="de480-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="de480-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="de480-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="de480-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="de480-110">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="de480-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="de480-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="de480-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="de480-112">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="de480-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="de480-113">[out] Liczba znaków, które faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="de480-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de480-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="de480-114">Requirements</span></span>  
 <span data-ttu-id="de480-115">**Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de480-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de480-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="de480-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de480-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="de480-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de480-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de480-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de480-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="de480-119">See Also</span></span>  
 [<span data-ttu-id="de480-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="de480-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="de480-121">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="de480-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
