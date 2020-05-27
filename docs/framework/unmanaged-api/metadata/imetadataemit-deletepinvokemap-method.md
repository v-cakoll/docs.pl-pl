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
ms.openlocfilehash: 79af7b5679598ffa82471dcb69adabc2394b13fa
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009304"
---
# <a name="imetadataemitdeletepinvokemap-method"></a><span data-ttu-id="32e3b-102">IMetaDataEmit::DeletePinvokeMap — Metoda</span><span class="sxs-lookup"><span data-stu-id="32e3b-102">IMetaDataEmit::DeletePinvokeMap Method</span></span>
<span data-ttu-id="32e3b-103">Niszczy metadane mapowania PInvoke dla obiektu, do którego odwołuje się określony token.</span><span class="sxs-lookup"><span data-stu-id="32e3b-103">Destroys the PInvoke mapping metadata for the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32e3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT DeletePinvokeMap (
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32e3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="32e3b-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="32e3b-106">podczas `mdFieldDef`Token lub `mdMethodDef` reprezentujący obiekt, dla którego mają zostać usunięte metadane mapowania PInvoke.</span><span class="sxs-lookup"><span data-stu-id="32e3b-106">[in] An `mdFieldDef` or `mdMethodDef` token that represents the object for which to delete the PInvoke mapping metadata.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32e3b-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32e3b-107">Requirements</span></span>  
 <span data-ttu-id="32e3b-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32e3b-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32e3b-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="32e3b-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="32e3b-110">**Biblioteka:** Używany jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="32e3b-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="32e3b-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32e3b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32e3b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32e3b-112">See also</span></span>

- [<span data-ttu-id="32e3b-113">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="32e3b-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="32e3b-114">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="32e3b-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
