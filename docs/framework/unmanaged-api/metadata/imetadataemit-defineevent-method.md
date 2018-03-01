---
title: "IMetaDataEmit::DefineEvent — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f27c0a01dd795cfcc5399c4115cd6d905629fd7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="744a9-102">IMetaDataEmit::DefineEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="744a9-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="744a9-103">Tworzy definicję zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="744a9-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="744a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="744a9-104">Syntax</span></span>  
  
```  
HRESULT DefineEvent (   
    [in]  mdTypeDef    td,   
    [in]  LPCWSTR      szEvent,   
    [in]  DWORD        dwEventFlags,   
    [in]  mdToken      tkEventType,   
    [in]  mdMethodDef  mdAddOn,   
    [in]  mdMethodDef  mdRemoveOn,   
    [in]  mdMethodDef  mdFire,   
    [in]  mdMethodDef  rmdOtherMethods[],   
    [out] mdEvent      *pmdEvent   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="744a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="744a9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="744a9-106">[in] Token dla klasy docelowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="744a9-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="744a9-107">Jest to `mdTypeDef` lub `mdTypeDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="744a9-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="744a9-108">[in] Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="744a9-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="744a9-109">[in] Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="744a9-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="744a9-110">[in] Token dla klasy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="744a9-110">[in] The token for the event class.</span></span> <span data-ttu-id="744a9-111">Jest to `mdTypeDef`, `mdTypeRef`, lub `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="744a9-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="744a9-112">[in] Metoda użyta do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="744a9-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="744a9-113">[in] Metoda używana do anulowania subskrypcji zdarzeń lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="744a9-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="744a9-114">[in] Metoda używana (przez klasę pochodną), aby wywołać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="744a9-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="744a9-115">[in] Tablica dla innych metod, skojarzone ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="744a9-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="744a9-116">Tablica kończy się znakiem `mdMethodDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="744a9-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="744a9-117">[out] Token metadanych przypisany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="744a9-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="744a9-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="744a9-118">Requirements</span></span>  
 <span data-ttu-id="744a9-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="744a9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="744a9-120">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="744a9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="744a9-121">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="744a9-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="744a9-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="744a9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="744a9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="744a9-123">See Also</span></span>  
 [<span data-ttu-id="744a9-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="744a9-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="744a9-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="744a9-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
