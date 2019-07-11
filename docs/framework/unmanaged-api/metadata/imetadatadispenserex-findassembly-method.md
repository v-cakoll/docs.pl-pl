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
ms.openlocfilehash: 85ebddf4ef96be2a583e54082e4d4405b30adf46
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777770"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="ac5d8-102">IMetaDataDispenserEx::FindAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac5d8-102">IMetaDataDispenserEx::FindAssembly Method</span></span>
<span data-ttu-id="ac5d8-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-103">This method is not implemented.</span></span> <span data-ttu-id="ac5d8-104">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac5d8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac5d8-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ac5d8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac5d8-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="ac5d8-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="ac5d8-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="ac5d8-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ac5d8-110">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="ac5d8-111">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ac5d8-112">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="ac5d8-113">[out] Liczba znaków rzeczywiście zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="ac5d8-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac5d8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac5d8-114">Requirements</span></span>  
 <span data-ttu-id="ac5d8-115">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac5d8-115">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac5d8-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ac5d8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ac5d8-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac5d8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ac5d8-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac5d8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac5d8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac5d8-119">See also</span></span>

- [<span data-ttu-id="ac5d8-120">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac5d8-120">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="ac5d8-121">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac5d8-121">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
