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
ms.openlocfilehash: f876187624d066b9e672fbf44a984d6d02a54c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175879"
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="cb9b1-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="cb9b1-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="cb9b1-103">Aktualizuje bieżący zakres zestawu ze zmianami wprowadzonymi w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="cb9b1-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb9b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb9b1-104">Syntax</span></span>  
  
```cpp  
HRESULT ApplyEditAndContinue (
    [in]  IUnknown    *pImport  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb9b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb9b1-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="cb9b1-106">\[w\] Wskaźnik do [IUnknown](/cpp/atl/iunknown) obiektu, który reprezentuje metadane delta z pliku pliku wykonywalnego przenośnego (PE).</span><span class="sxs-lookup"><span data-stu-id="cb9b1-106">\[in\] Pointer to an [IUnknown](/cpp/atl/iunknown) object that represents the delta metadata from the portable executable (PE) file.</span></span>
  
 <span data-ttu-id="cb9b1-107">Metadane różnicowe to blok metadanych, który zawiera zmiany wprowadzone do kopii rzeczywistych metadanych modułu.</span><span class="sxs-lookup"><span data-stu-id="cb9b1-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb9b1-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cb9b1-108">Requirements</span></span>  
 <span data-ttu-id="cb9b1-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb9b1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb9b1-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="cb9b1-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb9b1-111">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cb9b1-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cb9b1-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb9b1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9b1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb9b1-113">See also</span></span>

- [<span data-ttu-id="cb9b1-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="cb9b1-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="cb9b1-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cb9b1-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
