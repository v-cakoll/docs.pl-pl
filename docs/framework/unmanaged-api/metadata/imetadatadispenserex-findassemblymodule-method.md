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
ms.openlocfilehash: e73c95d8c720ed3263d6a66c48bdb5b5582eb686
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442181"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="ef2dc-102">IMetaDataDispenserEx::FindAssemblyModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="ef2dc-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="ef2dc-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-103">This method is not implemented.</span></span> <span data-ttu-id="ef2dc-104">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef2dc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef2dc-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="ef2dc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="ef2dc-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="ef2dc-107">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="ef2dc-108">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="ef2dc-109">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="ef2dc-110">podczas Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="ef2dc-111">podczas Zestaw, który ma zostać znaleziony.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="ef2dc-112">określoną Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ef2dc-113">podczas Rozmiar w bajtach `szName`.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="ef2dc-114">określoną Liczba znaków faktycznie zwróconych w `szName`.</span><span class="sxs-lookup"><span data-stu-id="ef2dc-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef2dc-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ef2dc-115">Requirements</span></span>  
 <span data-ttu-id="ef2dc-116">**Platforma:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef2dc-116">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef2dc-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ef2dc-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ef2dc-118">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef2dc-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ef2dc-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef2dc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef2dc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef2dc-120">See also</span></span>

- [<span data-ttu-id="ef2dc-121">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef2dc-121">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="ef2dc-122">IMetaDataDispenser, interfejs</span><span class="sxs-lookup"><span data-stu-id="ef2dc-122">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
