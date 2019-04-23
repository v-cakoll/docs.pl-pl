---
title: IMetaDataDispenserEx::FindAssemblyModule — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2d1d97e443be884f45187a2811ddfce106249515
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183134"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="36340-102">IMetaDataDispenserEx::FindAssemblyModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="36340-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="36340-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="36340-103">This method is not implemented.</span></span> <span data-ttu-id="36340-104">Jeżeli jest wywoływana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="36340-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36340-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="36340-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="36340-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="36340-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="36340-107">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="36340-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="36340-108">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="36340-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="36340-109">[in] Nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="36340-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="36340-110">[in] Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="36340-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="36340-111">[in] Zestaw, który ma zostać odnaleziona.</span><span class="sxs-lookup"><span data-stu-id="36340-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="36340-112">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="36340-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="36340-113">[in] Rozmiar w bajtach z `szName`.</span><span class="sxs-lookup"><span data-stu-id="36340-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="36340-114">[out] Liczba znaków rzeczywiście zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="36340-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36340-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="36340-115">Requirements</span></span>  
 <span data-ttu-id="36340-116">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36340-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36340-117">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="36340-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36340-118">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36340-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36340-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36340-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36340-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36340-120">See also</span></span>

- [<span data-ttu-id="36340-121">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="36340-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="36340-122">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="36340-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
