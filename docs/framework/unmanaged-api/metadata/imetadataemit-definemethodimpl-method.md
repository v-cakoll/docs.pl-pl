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
ms.openlocfilehash: e3a6f98dca1c6665b312384721a8fb590f914175
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468900"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="40ee4-102">IMetaDataEmit::DefineMethodImpl — Metoda</span><span class="sxs-lookup"><span data-stu-id="40ee4-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="40ee4-103">Tworzy definicję dla implementacji metody dziedziczone z interfejsu, a następnie zwraca token do tej definicji implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="40ee4-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ee4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40ee4-104">Syntax</span></span>  
  
```  
HRESULT DefineMethodImpl (   
    [in]  mdTypeDef         td,   
    [in]  mdToken           tkBody,   
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40ee4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="40ee4-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="40ee4-106">[in] `mdTypedef` Tokenu dla klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="40ee4-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="40ee4-107">[in] `mdMethodDef` Lub `mdMethodRef` tokenu treści kodu.</span><span class="sxs-lookup"><span data-stu-id="40ee4-107">[in] The `mdMethodDef` or `mdMethodRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="40ee4-108">[in] `mdMethodDef` Lub `mdMethodRef` token metody interfejsu implementowanego.</span><span class="sxs-lookup"><span data-stu-id="40ee4-108">[in] The `mdMethodDef` or `mdMethodRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40ee4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40ee4-109">Requirements</span></span>  
 <span data-ttu-id="40ee4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40ee4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40ee4-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="40ee4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="40ee4-112">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40ee4-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40ee4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40ee4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40ee4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40ee4-114">See also</span></span>
- [<span data-ttu-id="40ee4-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="40ee4-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="40ee4-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="40ee4-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
