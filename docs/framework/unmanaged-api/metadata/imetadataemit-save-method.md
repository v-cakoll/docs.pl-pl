---
title: IMetaDataEmit::Save — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Save
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Save
helpviewer_keywords:
- Save method, IMetaDataEmit interface [.NET Framework metadata]
- IMetaDataEmit::Save method [.NET Framework metadata]
ms.assetid: c1de8400-adfe-4a71-b828-a1d0cc1ea505
topic_type:
- apiref
ms.openlocfilehash: afd60cdf566bea459816ee890d44cc09258de516
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435946"
---
# <a name="imetadataemitsave-method"></a><span data-ttu-id="18776-102">IMetaDataEmit::Save — Metoda</span><span class="sxs-lookup"><span data-stu-id="18776-102">IMetaDataEmit::Save Method</span></span>
<span data-ttu-id="18776-103">Zapisuje wszystkie metadane w bieżącym zakresie do pliku pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="18776-103">Saves all metadata in the current scope to the file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18776-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="18776-104">Syntax</span></span>  
  
```cpp  
HRESULT Save (   
    [in]  LPCWSTR     szFile,   
    [in]  DWORD       dwSaveFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18776-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18776-105">Parameters</span></span>  
 `wzFile`  
 <span data-ttu-id="18776-106">podczas Nazwa pliku, w którym ma zostać zapisana.</span><span class="sxs-lookup"><span data-stu-id="18776-106">[in] The name of the file to save to.</span></span> <span data-ttu-id="18776-107">Jeśli ta wartość jest równa null, kopia znajdująca się w pamięci zostanie zapisana w ostatnio używanej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="18776-107">If this value is null, the in-memory copy will be saved to the last location that was used.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="18776-108">podczas Rezerwacj.</span><span class="sxs-lookup"><span data-stu-id="18776-108">[in] Reserved.</span></span> <span data-ttu-id="18776-109">Musi być równa zero.</span><span class="sxs-lookup"><span data-stu-id="18776-109">Must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18776-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="18776-110">Requirements</span></span>  
 <span data-ttu-id="18776-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18776-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18776-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="18776-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18776-113">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18776-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18776-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18776-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18776-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18776-115">See also</span></span>

- [<span data-ttu-id="18776-116">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="18776-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="18776-117">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="18776-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
