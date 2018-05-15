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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2ab66fecfaa66b5c56690950f6b19ecfd7e85e33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="a9158-102">IMetaDataEmit::DefineMethodImpl — Metoda</span><span class="sxs-lookup"><span data-stu-id="a9158-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="a9158-103">Tworzy definicję dla implementacji metody dziedziczone z interfejsem i zwraca token do tej definicji implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="a9158-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9158-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a9158-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9158-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a9158-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="a9158-106">[in] `mdTypedef` Token klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="a9158-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="a9158-107">[in] `mdMethodDef` Lub `mdMethodRef` token treści kodu.</span><span class="sxs-lookup"><span data-stu-id="a9158-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="a9158-108">[in] `mdMethodDef` Lub `mdMethodRef` token metody interfejsu implementowana.</span><span class="sxs-lookup"><span data-stu-id="a9158-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9158-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a9158-109">Requirements</span></span>  
 <span data-ttu-id="a9158-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9158-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9158-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a9158-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a9158-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9158-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a9158-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9158-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9158-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9158-114">See Also</span></span>  
 [<span data-ttu-id="a9158-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9158-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a9158-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a9158-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
