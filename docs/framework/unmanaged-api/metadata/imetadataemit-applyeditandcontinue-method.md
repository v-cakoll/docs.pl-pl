---
title: "IMetaDataEmit::ApplyEditAndContinue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.ApplyEditAndContinue
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::ApplyEditAndContinue
helpviewer_keywords:
- ApplyEditAndContinue method [.NET Framework metadata]
- IMetaDataEmit::ApplyEditAndContinue method [.NET Framework metadata]
ms.assetid: 35991289-f389-495d-8caa-a6384fb1d557
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b4d6f378c4da884cffc6827f700586cee745642b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitapplyeditandcontinue-method"></a><span data-ttu-id="ad465-102">IMetaDataEmit::ApplyEditAndContinue — Metoda</span><span class="sxs-lookup"><span data-stu-id="ad465-102">IMetaDataEmit::ApplyEditAndContinue Method</span></span>
<span data-ttu-id="ad465-103">Aktualizuje bieżącego zakresu zestawu zmian w określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="ad465-103">Updates the current assembly scope with the changes made in the specified metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad465-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad465-104">Syntax</span></span>  
  
```  
HRESULT ApplyEditAndContinue (   
    [in]  IUnknown    *pImport  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad465-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad465-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="ad465-106">[in] Wskaźnik do <<!--zzxref:IUnknown --> `IUnknown`> obiekt, który reprezentuje delta metadanych z pliku przenośny plik wykonywalny (PE).</span><span class="sxs-lookup"><span data-stu-id="ad465-106">[in] Pointer to an <<!--zzxref:IUnknown --> `IUnknown`> object that represents the delta metadata from the portable executable (PE) file.</span></span>  
  
 <span data-ttu-id="ad465-107">Metadane delta jest blok metadanych, które zawiera kopię rzeczywistego metadane modułu zostały wprowadzone zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad465-107">The delta metadata is the block of metadata that includes the changes that were made to the copy of the module's actual metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad465-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad465-108">Requirements</span></span>  
 <span data-ttu-id="ad465-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad465-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad465-110">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad465-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad465-111">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad465-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad465-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad465-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad465-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad465-113">See Also</span></span>  
 [<span data-ttu-id="ad465-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad465-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ad465-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad465-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
