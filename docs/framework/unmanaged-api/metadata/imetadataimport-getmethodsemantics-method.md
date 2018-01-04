---
title: "IMetaDataImport::GetMethodSemantics — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetMethodSemantics
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f8921c4f6a676c9647d4e8907a22f0d68b0b359
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="b7226-102">IMetaDataImport::GetMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="b7226-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="b7226-103">Pobiera flagi wskazujące relacji między metody odwołuje się określony token MethodDef i sparowanego właściwości i zdarzenia odwołuje się określony EventProp token.</span><span class="sxs-lookup"><span data-stu-id="b7226-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7226-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7226-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7226-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7226-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b7226-106">[in] Reprezentujący metodę, aby pobrać informacji o roli semantycznego dla tokenu MethodDef.</span><span class="sxs-lookup"><span data-stu-id="b7226-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="b7226-107">[in] Token reprezentujący sparowanego właściwości i zdarzeń, dla którego można pobrać metody roli.</span><span class="sxs-lookup"><span data-stu-id="b7226-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="b7226-108">[out] Wskaźnik do flag semantyki skojarzone.</span><span class="sxs-lookup"><span data-stu-id="b7226-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="b7226-109">Ta wartość jest maską bitów z [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b7226-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7226-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7226-110">Remarks</span></span>  
 <span data-ttu-id="b7226-111">[IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda Ustawia metodę flag semantyki.</span><span class="sxs-lookup"><span data-stu-id="b7226-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7226-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7226-112">Requirements</span></span>  
 <span data-ttu-id="b7226-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7226-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7226-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b7226-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b7226-115">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7226-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b7226-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7226-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7226-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7226-117">See Also</span></span>  
 [<span data-ttu-id="b7226-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7226-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="b7226-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="b7226-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
