---
title: IMetaDataEmit::DeleteFieldMarshal — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteFieldMarshal
helpviewer_keywords:
- IMetaDataEmit::DeleteFieldMarshal method [.NET Framework metadata]
- DeleteFieldMarshal method [.NET Framework metadata]
ms.assetid: 7c75aef9-c742-4b33-a14b-56ff94b0f725
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 36f9ac10348cb8235c95070ddbc9cb5f47a84bd6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777441"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="fdebb-102">IMetaDataEmit::DeleteFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="fdebb-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="fdebb-103">Niszczy PInvoke marshaling podpisu metadanych dla obiektu odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="fdebb-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdebb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdebb-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdebb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fdebb-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="fdebb-106">[in] `mdFieldDef` Lub `mdParamDef` token, który reprezentuje pole lub parametr, dla której chcesz usunąć organizowania podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="fdebb-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdebb-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdebb-107">Requirements</span></span>  
 <span data-ttu-id="fdebb-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdebb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdebb-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="fdebb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fdebb-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fdebb-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fdebb-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdebb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdebb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdebb-112">See also</span></span>

- [<span data-ttu-id="fdebb-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdebb-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fdebb-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fdebb-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
