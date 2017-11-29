---
title: "IMetaDataEmit::SetFieldProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetFieldProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5f031e79deab57184043eaa44d2d8a3d369187c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="96ce4-102">IMetaDataEmit::SetFieldProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="96ce4-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="96ce4-103">Ustawia lub aktualizuje wartość domyślna w polu odwołuje się token określonego pola.</span><span class="sxs-lookup"><span data-stu-id="96ce4-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96ce4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96ce4-104">Syntax</span></span>  
  
```  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,   
    [in]  DWORD       dwFieldFlags,   
    [in]  DWORD       dwCPlusTypeFlag,   
    [in]  void const  *pValue,   
    [in]  ULONG       cchValue   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96ce4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96ce4-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="96ce4-106">[in] Token pola docelowego.</span><span class="sxs-lookup"><span data-stu-id="96ce4-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="96ce4-107">[in] Atrybuty pól.</span><span class="sxs-lookup"><span data-stu-id="96ce4-107">[in] Field attributes.</span></span> <span data-ttu-id="96ce4-108">To jest maską bitów z `CorFieldAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="96ce4-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="96ce4-109">[in] `ELEMENT_TYPE_`  *\**  Wartości stałej.</span><span class="sxs-lookup"><span data-stu-id="96ce4-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="96ce4-110">Jest to `CorElementType` wartość.</span><span class="sxs-lookup"><span data-stu-id="96ce4-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="96ce4-111">Jeśli nie zdefiniowano jest stałą, ustaw tę wartość na `ELEMENT_TYPE_END`.</span><span class="sxs-lookup"><span data-stu-id="96ce4-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="96ce4-112">[in] Stała wartość dla pola.</span><span class="sxs-lookup"><span data-stu-id="96ce4-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="96ce4-113">[in] Rozmiar w znaki Unicode z `pValue`.</span><span class="sxs-lookup"><span data-stu-id="96ce4-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96ce4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96ce4-114">Requirements</span></span>  
 <span data-ttu-id="96ce4-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96ce4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96ce4-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96ce4-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96ce4-117">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="96ce4-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="96ce4-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96ce4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96ce4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96ce4-119">See Also</span></span>  
 [<span data-ttu-id="96ce4-120">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="96ce4-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="96ce4-121">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="96ce4-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
