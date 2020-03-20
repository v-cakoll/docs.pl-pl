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
ms.openlocfilehash: 47377e892aaf2bdd96a297630c47fe52215b0564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177378"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="da8fd-102">IMetaDataFilter::IsTokenMarked — Metoda</span><span class="sxs-lookup"><span data-stu-id="da8fd-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="da8fd-103">Pobiera wartość wskazującą, czy określony token metadanych został oznaczony jako przetworzony.</span><span class="sxs-lookup"><span data-stu-id="da8fd-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da8fd-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da8fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da8fd-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="da8fd-106">[w] Token do zbadania dla znaku przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="da8fd-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="da8fd-107">[na zewnątrz] Wartość, która `true` `tk` jest, jeśli została przetworzona; w `false`przeciwnym razie .</span><span class="sxs-lookup"><span data-stu-id="da8fd-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8fd-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da8fd-108">Requirements</span></span>  
 <span data-ttu-id="da8fd-109">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da8fd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da8fd-110">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="da8fd-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da8fd-111">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da8fd-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="da8fd-112">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da8fd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8fd-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da8fd-113">See also</span></span>

- [<span data-ttu-id="da8fd-114">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="da8fd-114">IMetaDataFilter Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatafilter-interface.md)
