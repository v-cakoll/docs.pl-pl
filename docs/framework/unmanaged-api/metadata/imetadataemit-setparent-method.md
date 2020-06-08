---
title: IMetaDataEmit::SetParent — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503851"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="d9030-102">IMetaDataEmit::SetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9030-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="d9030-103">Ustala, że określony element członkowski zdefiniowany przez poprzednie wywołanie do [IMetaDataEmit::D efinememberref](imetadataemit-definememberref-method.md), jest elementem członkowskim określonego typu, zdefiniowanym przez poprzednie wywołanie do [IMetaDataEmit::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="d9030-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9030-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9030-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9030-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9030-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="d9030-106">podczas `mdMemberRef`Token do otrzymania nowego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d9030-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="d9030-107">podczas `mdToken`Dla nowego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="d9030-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9030-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9030-108">Requirements</span></span>  
 <span data-ttu-id="d9030-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9030-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9030-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d9030-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d9030-111">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9030-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9030-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9030-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9030-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9030-113">See also</span></span>

- [<span data-ttu-id="d9030-114">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d9030-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d9030-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9030-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
