---
title: IMetaDataEmit::SetFieldRVA — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldRVA
helpviewer_keywords:
- IMetaDataEmit::SetFieldRVA method [.NET Framework metadata]
- SetFieldRVA method [.NET Framework metadata]
ms.assetid: 6dc37f9d-87ee-4cb3-9216-ced600184ce8
topic_type:
- apiref
ms.openlocfilehash: 501199bedec3b7a65d95c80cdef178831a65fd01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428421"
---
# <a name="imetadataemitsetfieldrva-method"></a><span data-ttu-id="c80e0-102">IMetaDataEmit::SetFieldRVA — Metoda</span><span class="sxs-lookup"><span data-stu-id="c80e0-102">IMetaDataEmit::SetFieldRVA Method</span></span>
<span data-ttu-id="c80e0-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span><span class="sxs-lookup"><span data-stu-id="c80e0-103">Sets a global variable value for the relative virtual address of the field referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c80e0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldRVA (   
    [in]  mdFieldDef  fd,   
    [in]  ULONG       ulRVA   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c80e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c80e0-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="c80e0-106">[in] The token for the target field.</span><span class="sxs-lookup"><span data-stu-id="c80e0-106">[in] The token for the target field.</span></span>  
  
 `ulRVA`  
 <span data-ttu-id="c80e0-107">[in] The address of a code or data area.</span><span class="sxs-lookup"><span data-stu-id="c80e0-107">[in] The address of a code or data area.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c80e0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c80e0-108">Requirements</span></span>  
 <span data-ttu-id="c80e0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c80e0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c80e0-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c80e0-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c80e0-111">**Library:** Used as a resource in MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c80e0-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c80e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c80e0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80e0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c80e0-113">See also</span></span>

- [<span data-ttu-id="c80e0-114">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="c80e0-114">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c80e0-115">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c80e0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
