---
title: IMetaDataImport::GetMethodSemantics — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437450"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="f0d87-102">IMetaDataImport::GetMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0d87-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="f0d87-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span><span class="sxs-lookup"><span data-stu-id="f0d87-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0d87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0d87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0d87-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="f0d87-106">[in] A MethodDef token representing the method to get the semantic role information for.</span><span class="sxs-lookup"><span data-stu-id="f0d87-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="f0d87-107">[in] A token representing the paired property and event for which to get the method's role.</span><span class="sxs-lookup"><span data-stu-id="f0d87-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="f0d87-108">[out] A pointer to the associated semantics flags.</span><span class="sxs-lookup"><span data-stu-id="f0d87-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="f0d87-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span><span class="sxs-lookup"><span data-stu-id="f0d87-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0d87-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0d87-110">Remarks</span></span>  
 <span data-ttu-id="f0d87-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span><span class="sxs-lookup"><span data-stu-id="f0d87-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d87-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0d87-112">Requirements</span></span>  
 <span data-ttu-id="f0d87-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d87-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d87-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="f0d87-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f0d87-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0d87-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f0d87-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d87-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d87-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d87-117">See also</span></span>

- [<span data-ttu-id="f0d87-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0d87-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="f0d87-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0d87-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
