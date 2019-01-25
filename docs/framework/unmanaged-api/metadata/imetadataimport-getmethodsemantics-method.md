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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a12310f1281da99706589894a4793c2a28c5b938
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745995"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="00816-102">IMetaDataImport::GetMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="00816-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="00816-103">Pobiera flagi wskazującą związek między odwołuje się określony token MethodDef oraz sparowany właściwości, metody i zdarzenia odwołuje się określona EventProp token.</span><span class="sxs-lookup"><span data-stu-id="00816-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00816-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00816-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00816-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00816-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="00816-106">[in] Token MethodDef reprezentujący metodę, które mają być pobrane informacje semantyczne roli.</span><span class="sxs-lookup"><span data-stu-id="00816-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="00816-107">[in] Token reprezentujący par właściwości i zdarzenia, dla którego należy pobrać rolę metody.</span><span class="sxs-lookup"><span data-stu-id="00816-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="00816-108">[out] Wskaźnik flagi skojarzone semantyki.</span><span class="sxs-lookup"><span data-stu-id="00816-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="00816-109">Ta wartość jest z [cormethodsemanticsattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="00816-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00816-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00816-110">Remarks</span></span>  
 <span data-ttu-id="00816-111">[IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metody Ustawia flagi semantyki metody.</span><span class="sxs-lookup"><span data-stu-id="00816-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00816-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00816-112">Requirements</span></span>  
 <span data-ttu-id="00816-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00816-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00816-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="00816-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00816-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00816-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00816-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00816-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00816-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00816-117">See also</span></span>
- [<span data-ttu-id="00816-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="00816-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="00816-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="00816-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
