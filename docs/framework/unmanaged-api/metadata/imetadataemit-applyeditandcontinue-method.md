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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: faa9bc412e67e0e49ee969bd8b246a424fe628a0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109121"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="ee19f-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="ee19f-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="ee19f-103">Aktualizuje bieżącego zakresu zestawu zmian wprowadzonych w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="ee19f-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee19f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ee19f-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ee19f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ee19f-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="ee19f-106">\[w\] wskaźnik do [IUnknown](/cpp/atl/iunknown) obiekt, który reprezentuje metadane różnicowych z plików przenośnych plików wykonywalnych (PE).</span><span class="sxs-lookup"><span data-stu-id="ee19f-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="ee19f-107">Metadane różnicowe są blok metadanych, który zawiera zmiany, które zostały wprowadzone na kopię rzeczywistego metadane modułu.</span><span class="sxs-lookup"><span data-stu-id="ee19f-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee19f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee19f-108">Requirements</span></span>  
 <span data-ttu-id="ee19f-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee19f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee19f-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ee19f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ee19f-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ee19f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee19f-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee19f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee19f-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ee19f-113">See Also</span></span>  
 [<span data-ttu-id="ee19f-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee19f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ee19f-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee19f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
