---
title: IMetaDataEmit::DeletePinvokeMap — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeletePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeletePinvokeMap
helpviewer_keywords:
- IMetaDataEmit::DeletePinvokeMap method [.NET Framework metadata]
- DeletePinvokeMap method [.NET Framework metadata]
ms.assetid: 3c4f6b54-5ce7-4a2a-83e1-6dec16441f50
topic_type:
- apiref
ms.openlocfilehash: 1621e955795fcdbb651114c60eb6a1126a23d037
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434362"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="51318-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="51318-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="51318-103">Niszczy metadane mapowania PInvoke dla obiektu, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="51318-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51318-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51318-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (   
    [in]  mdToken     tk   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51318-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51318-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="51318-106">podczas Token `mdFieldDef` lub `mdMethodDef` reprezentujący obiekt, dla którego mają zostać usunięte metadane mapowania funkcji PInvoke.</span><span class="sxs-lookup"><span data-stu-id="51318-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51318-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51318-107">Requirements</span></span>  
 <span data-ttu-id="51318-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51318-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51318-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="51318-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51318-110">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="51318-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51318-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51318-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51318-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51318-112">See also</span></span>

- [<span data-ttu-id="51318-113">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="51318-113">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="51318-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="51318-114">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
