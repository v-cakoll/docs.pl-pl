---
title: IMetaDataImport::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 8360a74e9e18e5b68ecc9edd7be2e3a711cb61c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437780"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="3b4ea-102">IMetaDataImport::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="3b4ea-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="3b4ea-103">Gets layout information for the class referenced by the specified TypeDef token.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b4ea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3b4ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b4ea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3b4ea-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3b4ea-106">[in] The TypeDef token for the class with the layout to return.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="3b4ea-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="3b4ea-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3b4ea-109">[in] The maximum size of the `rFieldOffset` array.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="3b4ea-110">[out] The number of elements returned in `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="3b4ea-111">[out] The size in bytes of the class represented by `td`.</span><span class="sxs-lookup"><span data-stu-id="3b4ea-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b4ea-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3b4ea-112">Requirements</span></span>  
 <span data-ttu-id="3b4ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b4ea-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b4ea-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b4ea-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b4ea-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b4ea-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b4ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b4ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b4ea-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b4ea-117">See also</span></span>

- [<span data-ttu-id="3b4ea-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b4ea-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3b4ea-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3b4ea-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
