---
title: IMetaDataEmit::DefineEvent — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ba35cd678d88389854ca2e866020ea3a9364c923
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777662"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="abe64-102">IMetaDataEmit::DefineEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="abe64-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="abe64-103">Tworzy definicję na zdarzenie o sygnaturze określonych metadanych, a następnie pobiera token do tej definicji zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="abe64-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe64-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abe64-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="abe64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abe64-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="abe64-106">[in] Token dla klasy docelowej lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="abe64-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="abe64-107">Jest to `mdTypeDef` lub `mdTypeDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="abe64-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="abe64-108">[in] Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="abe64-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="abe64-109">[in] Flagi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="abe64-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="abe64-110">[in] Token dla klasy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="abe64-110">[in] The token for the event class.</span></span> <span data-ttu-id="abe64-111">Jest to `mdTypeDef`, `mdTypeRef`, lub `mdTokenNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="abe64-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="abe64-112">[in] Metoda używana do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="abe64-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="abe64-113">[in] Metoda użyta Aby anulować subskrypcję zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="abe64-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="abe64-114">[in] Metoda używana (przez klasę pochodną), aby zgłosić zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="abe64-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="abe64-115">[in] Tablica do innych metod, skojarzone ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="abe64-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="abe64-116">Tablica jest kończony przy użyciu `mdMethodDefNil` tokenu.</span><span class="sxs-lookup"><span data-stu-id="abe64-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="abe64-117">[out] Token metadanych, przypisany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="abe64-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe64-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abe64-118">Requirements</span></span>  
 <span data-ttu-id="abe64-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe64-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe64-120">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="abe64-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abe64-121">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="abe64-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abe64-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe64-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe64-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abe64-123">See also</span></span>

- [<span data-ttu-id="abe64-124">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="abe64-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="abe64-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="abe64-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
