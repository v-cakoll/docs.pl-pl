---
title: "IMetaDataEmit::DefineUserString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefineUserString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 729f2d48722fb34b844636b416edf36d715e1a48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="66f3b-102">IMetaDataEmit::DefineUserString — Metoda</span><span class="sxs-lookup"><span data-stu-id="66f3b-102">IMetaDataEmit::DefineUserString Method</span></span>
<span data-ttu-id="66f3b-103">Pobiera metadane token dla określonego ciągu literału.</span><span class="sxs-lookup"><span data-stu-id="66f3b-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66f3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66f3b-104">Syntax</span></span>  
  
```  
HRESULT DefineUserString (   
    [in]  LPCWSTR     szString,   
    [in]  ULONG       cchString,   
    [out] mdString    *pstk   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66f3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66f3b-105">Parameters</span></span>  
 `szString`  
 <span data-ttu-id="66f3b-106">[in] Ciąg użytkownika do przechowywania.</span><span class="sxs-lookup"><span data-stu-id="66f3b-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="66f3b-107">[in] Liczba znaki dwubajtowe w `szString`.</span><span class="sxs-lookup"><span data-stu-id="66f3b-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="66f3b-108">[out] Token ciągu przypisany.</span><span class="sxs-lookup"><span data-stu-id="66f3b-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66f3b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66f3b-109">Requirements</span></span>  
 <span data-ttu-id="66f3b-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66f3b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66f3b-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="66f3b-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="66f3b-112">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66f3b-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66f3b-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66f3b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66f3b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66f3b-114">See Also</span></span>  
 [<span data-ttu-id="66f3b-115">IMetaDataEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="66f3b-115">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="66f3b-116">IMetaDataEmit2, interfejs</span><span class="sxs-lookup"><span data-stu-id="66f3b-116">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
