---
title: IMetaDataEmit::ApplyEditAndContinue — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.ApplyEditAndContinue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type:
- apiref
ms.openlocfilehash: b9cad4c9647983e5b39f9b7a5d03736f2848e1c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432699"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="cb692-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb692-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="cb692-103">Aktualizuje bieżący zakres zestawu zmianami wprowadzonymi w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="cb692-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb692-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb692-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb692-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb692-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="cb692-106">\[w\] wskaźnik do obiektu [IUnknown](/cpp/atl/iunknown) , który reprezentuje metadane różnicowe z przenośnego pliku wykonywalnego (PE).</span><span class="sxs-lookup"><span data-stu-id="cb692-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="cb692-107">Metadane różnicowe to blok metadanych, który zawiera zmiany wprowadzone w kopii rzeczywistych metadanych modułu.</span><span class="sxs-lookup"><span data-stu-id="cb692-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb692-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb692-108">Requirements</span></span>  
 <span data-ttu-id="cb692-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb692-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb692-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb692-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb692-111">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cb692-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb692-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb692-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb692-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb692-113">See also</span></span>

- [<span data-ttu-id="cb692-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb692-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cb692-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb692-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
