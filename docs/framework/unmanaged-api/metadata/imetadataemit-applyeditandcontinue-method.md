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
ms.openlocfilehash: c18c72ecbaf2e0d3153ad7f00caf73421e35fa0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225316"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="47a5f-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="47a5f-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="47a5f-103">Aktualizuje bieżącego zakresu zestawu zmian wprowadzonych w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="47a5f-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47a5f-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="47a5f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="47a5f-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="47a5f-106">\[w\] wskaźnik do [IUnknown](/cpp/atl/iunknown) obiekt, który reprezentuje metadane różnicowych z plików przenośnych plików wykonywalnych (PE).</span><span class="sxs-lookup"><span data-stu-id="47a5f-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="47a5f-107">Metadane różnicowe są blok metadanych, który zawiera zmiany, które zostały wprowadzone na kopię rzeczywistego metadane modułu.</span><span class="sxs-lookup"><span data-stu-id="47a5f-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a5f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47a5f-108">Requirements</span></span>  
 <span data-ttu-id="47a5f-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a5f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a5f-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="47a5f-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47a5f-111">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="47a5f-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="47a5f-112">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="47a5f-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="47a5f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47a5f-113">See also</span></span>

- [<span data-ttu-id="47a5f-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="47a5f-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="47a5f-115">IMetaDataEmit2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="47a5f-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
