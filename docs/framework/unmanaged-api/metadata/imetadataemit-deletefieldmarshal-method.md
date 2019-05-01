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
ms.openlocfilehash: 78f2405bba9172b775b01e5417860c3f3d2dd4a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992527"
---
# <a name="imetadataemitdeletefieldmarshal-method"></a><span data-ttu-id="f0230-102">IMetaDataEmit::DeleteFieldMarshal — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0230-102">IMetaDataEmit::DeleteFieldMarshal Method</span></span>
<span data-ttu-id="f0230-103">Niszczy PInvoke marshaling podpisu metadanych dla obiektu odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="f0230-103">Destroys the PInvoke marshaling metadata signature for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0230-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0230-104">Syntax</span></span>  
  
```  
HRESULT DeleteFieldMarshal (  
    [in]  mdToken     tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0230-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0230-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f0230-106">[in] `mdFieldDef` Lub `mdParamDef` token, który reprezentuje pole lub parametr, dla której chcesz usunąć organizowania podpisu metadanych.</span><span class="sxs-lookup"><span data-stu-id="f0230-106">[in] An `mdFieldDef` or `mdParamDef` token that represents the field or parameter for which to delete the marshaling metadata signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0230-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0230-107">Requirements</span></span>  
 <span data-ttu-id="f0230-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0230-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0230-109">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f0230-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0230-110">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0230-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0230-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0230-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0230-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0230-112">See also</span></span>

- [<span data-ttu-id="f0230-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0230-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f0230-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0230-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
