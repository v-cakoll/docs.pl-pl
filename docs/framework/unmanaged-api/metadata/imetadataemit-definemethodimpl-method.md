---
title: IMetaDataEmit::DefineMethodImpl — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 64d76efa8c2f29fda559e5c84217b865540027ba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175827"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="9b547-102">IMetaDataEmit::DefineMethodImpl — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b547-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="9b547-103">Tworzy definicję implementacji metody dziedziczonej z interfejsu i zwraca token do tej definicji implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="9b547-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b547-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b547-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b547-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b547-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="9b547-106">[w] Token `mdTypedef` klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="9b547-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="9b547-107">[w] `mdMethodDef` Lub `mdMemberRef` token treści kodu.</span><span class="sxs-lookup"><span data-stu-id="9b547-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="9b547-108">[w] Lub `mdMethodDef` `mdMemberRef` token metody interfejsu implementowane.</span><span class="sxs-lookup"><span data-stu-id="9b547-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b547-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b547-109">Requirements</span></span>  
 <span data-ttu-id="9b547-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b547-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b547-111">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="9b547-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9b547-112">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b547-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b547-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b547-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b547-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b547-114">See also</span></span>

- [<span data-ttu-id="9b547-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9b547-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="9b547-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b547-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
