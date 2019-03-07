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
ms.openlocfilehash: d0558154dc64ca95a691f36fb67586d570caa888
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484995"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="685d0-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="685d0-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="685d0-103">Aktualizuje bieżącego zakresu zestawu zmian wprowadzonych w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="685d0-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="685d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="685d0-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="685d0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="685d0-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="685d0-106">\[w\] wskaźnik do [IUnknown](/cpp/atl/iunknown) obiekt, który reprezentuje metadane różnicowych z plików przenośnych plików wykonywalnych (PE).</span><span class="sxs-lookup"><span data-stu-id="685d0-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="685d0-107">Metadane różnicowe są blok metadanych, który zawiera zmiany, które zostały wprowadzone na kopię rzeczywistego metadane modułu.</span><span class="sxs-lookup"><span data-stu-id="685d0-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="685d0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="685d0-108">Requirements</span></span>  
 <span data-ttu-id="685d0-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="685d0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="685d0-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="685d0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="685d0-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="685d0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="685d0-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="685d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="685d0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="685d0-113">See also</span></span>
- [<span data-ttu-id="685d0-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="685d0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="685d0-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="685d0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
