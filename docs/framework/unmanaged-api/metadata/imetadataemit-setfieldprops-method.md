---
title: IMetaDataEmit::SetFieldProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: b921118f7c43edef3c07cbb34cbbd9119d36ce51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177551"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="fc4a6-102">IMetaDataEmit::SetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="fc4a6-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="fc4a6-103">Ustawia lub aktualizuje wartość domyślną dla pola, do którego odwołuje się określony token pola.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc4a6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc4a6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc4a6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc4a6-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="fc4a6-106">[w] Token dla pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="fc4a6-107">[w] Atrybuty pola.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-107">[in] Field attributes.</span></span> <span data-ttu-id="fc4a6-108">Jest to maska `CorFieldAttr` bitowa wartości.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="fc4a6-109">[w] Dla `ELEMENT_TYPE_` *\** wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="fc4a6-110">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="fc4a6-111">Jeśli stała nie jest definiowana, `ELEMENT_TYPE_END`ustaw tę wartość na .</span><span class="sxs-lookup"><span data-stu-id="fc4a6-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="fc4a6-112">[w] Stała wartość pola.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="fc4a6-113">[w] Rozmiar w znakach Unicode `pValue`.</span><span class="sxs-lookup"><span data-stu-id="fc4a6-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc4a6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc4a6-114">Requirements</span></span>  
 <span data-ttu-id="fc4a6-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc4a6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc4a6-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="fc4a6-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc4a6-117">**Biblioteka:** Używany jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc4a6-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc4a6-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc4a6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc4a6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc4a6-119">See also</span></span>

- [<span data-ttu-id="fc4a6-120">IMetaDataEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fc4a6-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="fc4a6-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc4a6-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
