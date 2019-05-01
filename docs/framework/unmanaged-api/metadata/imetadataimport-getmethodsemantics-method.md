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
ms.openlocfilehash: 57ddbd8c6935f2c0275c132e30ea175c6f198fac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777705"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="1cd93-102">IMetaDataImport::GetMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="1cd93-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="1cd93-103">Pobiera flagi wskazującą związek między odwołuje się określony token MethodDef oraz sparowany właściwości, metody i zdarzenia odwołuje się określona EventProp token.</span><span class="sxs-lookup"><span data-stu-id="1cd93-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd93-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cd93-104">Syntax</span></span>  
  
```  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cd93-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cd93-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="1cd93-106">[in] Token MethodDef reprezentujący metodę, które mają być pobrane informacje semantyczne roli.</span><span class="sxs-lookup"><span data-stu-id="1cd93-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="1cd93-107">[in] Token reprezentujący par właściwości i zdarzenia, dla którego należy pobrać rolę metody.</span><span class="sxs-lookup"><span data-stu-id="1cd93-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="1cd93-108">[out] Wskaźnik flagi skojarzone semantyki.</span><span class="sxs-lookup"><span data-stu-id="1cd93-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="1cd93-109">Ta wartość jest z [cormethodsemanticsattr —](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="1cd93-109">This value is a bitmask from the [CorMethodSemanticsAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cd93-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cd93-110">Remarks</span></span>  
 <span data-ttu-id="1cd93-111">[IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metody Ustawia flagi semantyki metody.</span><span class="sxs-lookup"><span data-stu-id="1cd93-111">The [IMetaDataEmit::DefineProperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cd93-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1cd93-112">Requirements</span></span>  
 <span data-ttu-id="1cd93-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cd93-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cd93-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="1cd93-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1cd93-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cd93-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1cd93-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cd93-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cd93-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cd93-117">See also</span></span>

- [<span data-ttu-id="1cd93-118">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="1cd93-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="1cd93-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1cd93-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
