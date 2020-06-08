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
ms.openlocfilehash: 2cfb66203d8f2d69ea188f6913a5ef34dd74791e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503604"
---
# <a name="imetadataimportgetmethodsemantics-method"></a><span data-ttu-id="0c1ad-102">IMetaDataImport::GetMethodSemantics — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c1ad-102">IMetaDataImport::GetMethodSemantics Method</span></span>
<span data-ttu-id="0c1ad-103">Pobiera flagi wskazujące relację między metodą przywoływaną przez określony token MethodDef i sparowaną właściwością i zdarzeniem, do którego odwołuje się określony token EventProp.</span><span class="sxs-lookup"><span data-stu-id="0c1ad-103">Gets flags indicating the relationship between the method referenced by the specified MethodDef token and the paired property and event referenced by the specified EventProp token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c1ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c1ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c1ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c1ad-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="0c1ad-106">podczas Token MethodDef reprezentujący metodę uzyskiwania informacji o roli semantycznej dla.</span><span class="sxs-lookup"><span data-stu-id="0c1ad-106">[in] A MethodDef token representing the method to get the semantic role information for.</span></span>  
  
 `tkEventProp`  
 <span data-ttu-id="0c1ad-107">podczas Token reprezentujący sparowaną Właściwość i zdarzenie, dla którego ma zostać uzyskana rola metody.</span><span class="sxs-lookup"><span data-stu-id="0c1ad-107">[in] A token representing the paired property and event for which to get the method's role.</span></span>  
  
 `pdwSemanticsFlags`  
 <span data-ttu-id="0c1ad-108">określoną Wskaźnik do skojarzonych flag semantycznych.</span><span class="sxs-lookup"><span data-stu-id="0c1ad-108">[out] A pointer to the associated semantics flags.</span></span> <span data-ttu-id="0c1ad-109">Ta wartość jest maska bitowa z wyliczenia [CorMethodSemanticsAttr —](cormethodsemanticsattr-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0c1ad-109">This value is a bitmask from the [CorMethodSemanticsAttr](cormethodsemanticsattr-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c1ad-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c1ad-110">Remarks</span></span>  
 <span data-ttu-id="0c1ad-111">[IMetaDataEmit::D efineproperty](imetadataemit-defineproperty-method.md) Metoda ustawia flagi semantyki metody.</span><span class="sxs-lookup"><span data-stu-id="0c1ad-111">The [IMetaDataEmit::DefineProperty](imetadataemit-defineproperty-method.md) method sets a method's semantics flags.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c1ad-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c1ad-112">Requirements</span></span>  
 <span data-ttu-id="0c1ad-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c1ad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c1ad-114">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0c1ad-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0c1ad-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0c1ad-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0c1ad-116">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c1ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1ad-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c1ad-117">See also</span></span>

- [<span data-ttu-id="0c1ad-118">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c1ad-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0c1ad-119">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c1ad-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
