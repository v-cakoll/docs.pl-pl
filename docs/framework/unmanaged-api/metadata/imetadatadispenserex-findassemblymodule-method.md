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
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006184"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a><span data-ttu-id="44b92-102">IMetaDataDispenserEx::FindAssemblyModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="44b92-102">IMetaDataDispenserEx::FindAssemblyModule Method</span></span>
<span data-ttu-id="44b92-103">Ta metoda nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="44b92-103">This method is not implemented.</span></span> <span data-ttu-id="44b92-104">Jeśli zostanie wywołana, zwraca E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="44b92-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b92-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="44b92-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="44b92-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="44b92-106">Parameters</span></span>  
 `szAppBase`  
 <span data-ttu-id="44b92-107">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="44b92-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="44b92-108">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="44b92-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="44b92-109">podczas Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="44b92-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="44b92-110">podczas Nazwa modułu.</span><span class="sxs-lookup"><span data-stu-id="44b92-110">[in] The name of the module.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="44b92-111">podczas Zestaw, który ma zostać znaleziony.</span><span class="sxs-lookup"><span data-stu-id="44b92-111">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="44b92-112">określoną Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="44b92-112">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="44b92-113">podczas Rozmiar, w bajtach, z `szName` .</span><span class="sxs-lookup"><span data-stu-id="44b92-113">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="44b92-114">określoną Liczba znaków, które faktycznie zostały zwrócone `szName` .</span><span class="sxs-lookup"><span data-stu-id="44b92-114">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44b92-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44b92-115">Requirements</span></span>  
 <span data-ttu-id="44b92-116">**Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b92-116">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b92-117">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="44b92-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44b92-118">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="44b92-118">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="44b92-119">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44b92-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44b92-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44b92-120">See also</span></span>

- [<span data-ttu-id="44b92-121">IMetaDataDispenserEx, interfejs</span><span class="sxs-lookup"><span data-stu-id="44b92-121">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="44b92-122">IMetaDataDispenser — Interfejs</span><span class="sxs-lookup"><span data-stu-id="44b92-122">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
