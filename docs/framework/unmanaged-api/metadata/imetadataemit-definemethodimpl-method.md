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
ms.openlocfilehash: 5ed5afbbf49b6680d00e78b6af3d45c6f0a7229d
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004494"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="04fc3-102">IMetaDataEmit::DefineMethodImpl — Metoda</span><span class="sxs-lookup"><span data-stu-id="04fc3-102">IMetaDataEmit::DefineMethodImpl Method</span></span>
<span data-ttu-id="04fc3-103">Tworzy definicję dla implementacji metody dziedziczonej z interfejsu i zwraca token do tej definicji implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="04fc3-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04fc3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04fc3-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04fc3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04fc3-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="04fc3-106">podczas `mdTypedef`Token klasy implementującej.</span><span class="sxs-lookup"><span data-stu-id="04fc3-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="04fc3-107">podczas `mdMethodDef`Token lub `mdMemberRef` treść kodu.</span><span class="sxs-lookup"><span data-stu-id="04fc3-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="04fc3-108">podczas `mdMethodDef`Token lub `mdMemberRef` metoda interfejsu, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="04fc3-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04fc3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04fc3-109">Requirements</span></span>  
 <span data-ttu-id="04fc3-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04fc3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04fc3-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04fc3-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04fc3-112">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04fc3-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04fc3-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04fc3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04fc3-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04fc3-114">See also</span></span>

- [<span data-ttu-id="04fc3-115">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="04fc3-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="04fc3-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="04fc3-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
