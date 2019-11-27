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
ms.openlocfilehash: a73afaebc2943190eeeee50367ecd31f1fb59df1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432442"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="83162-102">IMetaDataEmit::SetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="83162-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="83162-103">Ustala, że określony element członkowski zdefiniowany przez poprzednie wywołanie do [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), jest elementem członkowskim określonego typu, zdefiniowanym przez poprzednie wywołanie do [IMetaDataEmit::D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="83162-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83162-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83162-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (   
    [in]  mdMemberRef mr,   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83162-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83162-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="83162-106">podczas Token `mdMemberRef` do otrzymania nowego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="83162-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="83162-107">podczas `mdToken` dla nowego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="83162-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83162-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83162-108">Requirements</span></span>  
 <span data-ttu-id="83162-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83162-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83162-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="83162-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83162-111">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="83162-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83162-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83162-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83162-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83162-113">See also</span></span>

- [<span data-ttu-id="83162-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="83162-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="83162-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="83162-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
