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
ms.openlocfilehash: 7babd0a90b9882acb03b6360753f55c57a399b9e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005638"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="ffc01-102">IMetaDataEmit::DefineEvent — Metoda</span><span class="sxs-lookup"><span data-stu-id="ffc01-102">IMetaDataEmit::DefineEvent Method</span></span>
<span data-ttu-id="ffc01-103">Tworzy definicję zdarzenia z określonym podpisem metadanych i pobiera token do tej definicji zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ffc01-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffc01-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ffc01-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ffc01-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ffc01-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ffc01-106">podczas Token dla docelowej klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ffc01-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="ffc01-107">Jest to `mdTypeDef` `mdTypeDefNil` token lub.</span><span class="sxs-lookup"><span data-stu-id="ffc01-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="ffc01-108">podczas Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ffc01-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="ffc01-109">podczas Flagi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ffc01-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="ffc01-110">podczas Token dla klasy Event.</span><span class="sxs-lookup"><span data-stu-id="ffc01-110">[in] The token for the event class.</span></span> <span data-ttu-id="ffc01-111">Jest to `mdTypeDef` , a `mdTypeRef` , lub `mdTokenNil` token.</span><span class="sxs-lookup"><span data-stu-id="ffc01-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="ffc01-112">podczas Metoda używana do subskrybowania zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="ffc01-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="ffc01-113">podczas Metoda używana do anulowania subskrypcji zdarzenia lub wartość null.</span><span class="sxs-lookup"><span data-stu-id="ffc01-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="ffc01-114">podczas Metoda używana (przez klasę pochodną) do podniesienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ffc01-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="ffc01-115">podczas Tablica tokenów dla innych metod skojarzonych ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="ffc01-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="ffc01-116">Tablica została zakończona z `mdMethodDefNil` tokenem.</span><span class="sxs-lookup"><span data-stu-id="ffc01-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="ffc01-117">określoną Token metadanych przypisany do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ffc01-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffc01-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ffc01-118">Requirements</span></span>  
 <span data-ttu-id="ffc01-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ffc01-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ffc01-120">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="ffc01-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ffc01-121">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ffc01-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ffc01-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ffc01-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc01-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ffc01-123">See also</span></span>

- [<span data-ttu-id="ffc01-124">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ffc01-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ffc01-125">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="ffc01-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
