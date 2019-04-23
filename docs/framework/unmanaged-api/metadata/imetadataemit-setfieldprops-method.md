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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 94ba607669b4b1ca68294470cf1cc4fb27464d28
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097658"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="33bc2-102">IMetaDataEmit::SetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="33bc2-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="33bc2-103">Ustawia lub aktualizuje wartość domyślną dla pola przywoływane przez token określonego pola.</span><span class="sxs-lookup"><span data-stu-id="33bc2-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33bc2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33bc2-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33bc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33bc2-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="33bc2-106">[in] Token do pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="33bc2-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="33bc2-107">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="33bc2-107">[in] Field attributes.</span></span> <span data-ttu-id="33bc2-108">Jest to z `CorFieldAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="33bc2-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="33bc2-109">[in] `ELEMENT_TYPE_` *\** Wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="33bc2-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="33bc2-110">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="33bc2-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="33bc2-111">Jeśli nie zdefiniowano jest stałą, ustaw tę wartość na `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="33bc2-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="33bc2-112">[in] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="33bc2-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="33bc2-113">[in] Rozmiar w znaki Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="33bc2-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33bc2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33bc2-114">Requirements</span></span>  
 <span data-ttu-id="33bc2-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33bc2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33bc2-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="33bc2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="33bc2-117">**Biblioteka:** Używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="33bc2-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33bc2-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33bc2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33bc2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33bc2-119">See also</span></span>

- [<span data-ttu-id="33bc2-120">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="33bc2-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="33bc2-121">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="33bc2-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
