---
title: IMetaDataFilter::IsTokenMarked — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.IsTokenMarked
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::IsTokenMarked
helpviewer_keywords:
- IMetaDataFilter::IsTokenMarked method [.NET Framework metadata]
- IsTokenMarked method [.NET Framework metadata]
ms.assetid: 7d90dcee-0206-4540-807b-06982fe65f1a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 32642c4ff6193e2002c8a4c7d201b36c7601debb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582542"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="d52be-102">IMetaDataFilter::IsTokenMarked — Metoda</span><span class="sxs-lookup"><span data-stu-id="d52be-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="d52be-103">Pobiera wartość wskazującą, czy token określonych metadanych została oznaczona jako przetworzona.</span><span class="sxs-lookup"><span data-stu-id="d52be-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d52be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d52be-104">Syntax</span></span>  
  
```  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,   
    [out] BOOL     *pIsMarked  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d52be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d52be-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="d52be-106">[in] Token do zbadania znaku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d52be-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="d52be-107">[out] Wartość, która jest `true` Jeśli `tk` zostało przetworzone; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d52be-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d52be-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d52be-108">Requirements</span></span>  
 <span data-ttu-id="d52be-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52be-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52be-110">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="d52be-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d52be-111">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d52be-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d52be-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d52be-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52be-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d52be-113">See also</span></span>
- [<span data-ttu-id="d52be-114">IMetaDataFilter, interfejs</span><span class="sxs-lookup"><span data-stu-id="d52be-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
