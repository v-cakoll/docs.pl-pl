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
ms.openlocfilehash: a9598be850604f16ee8cc62187e1fed7ecf3a7e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175853"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="9551b-102">IMetaDataEmit::DefineEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="9551b-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="9551b-103">Tworzy definicję zdarzenia z określonym podpisem metadanych i pobiera token do tej definicji zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9551b-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9551b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9551b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9551b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9551b-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9551b-106">[w] Token dla klasy docelowej lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9551b-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="9551b-107">Jest to token `mdTypeDef` `mdTypeDefNil` lub token.</span><span class="sxs-lookup"><span data-stu-id="9551b-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="9551b-108">[w] Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9551b-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="9551b-109">[w] Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9551b-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="9551b-110">[w] Token dla klasy zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9551b-110">[in] The token for the event class.</span></span> <span data-ttu-id="9551b-111">Jest to `mdTypeDef`, `mdTypeRef`a `mdTokenNil` , lub token.</span><span class="sxs-lookup"><span data-stu-id="9551b-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="9551b-112">[w] Metoda używana do subskrybowania zdarzenia lub null.</span><span class="sxs-lookup"><span data-stu-id="9551b-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="9551b-113">[w] Metoda używana do anulowania subskrypcji zdarzenia lub null.</span><span class="sxs-lookup"><span data-stu-id="9551b-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="9551b-114">[w] Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9551b-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="9551b-115">[w] Tablica tokenów dla innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="9551b-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="9551b-116">Tablica zostanie zakończona `mdMethodDefNil` tokenem.</span><span class="sxs-lookup"><span data-stu-id="9551b-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="9551b-117">[na zewnątrz] Token metadanych przypisany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9551b-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9551b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9551b-118">Requirements</span></span>  
 <span data-ttu-id="9551b-119">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9551b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9551b-120">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="9551b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9551b-121">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9551b-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9551b-122">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9551b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9551b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9551b-123">See also</span></span>

- [<span data-ttu-id="9551b-124">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9551b-124">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9551b-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9551b-125">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
