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
ms.openlocfilehash: eb0ebab0f4e05d81730d5beb2b5345e319e8e274
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492541"
---
# <a name="imetadatafilteristokenmarked-method"></a><span data-ttu-id="f35f6-102">IMetaDataFilter::IsTokenMarked — Metoda</span><span class="sxs-lookup"><span data-stu-id="f35f6-102">IMetaDataFilter::IsTokenMarked Method</span></span>
<span data-ttu-id="f35f6-103">Pobiera wartość wskazującą, czy określony token metadanych został oznaczony jako przetworzony.</span><span class="sxs-lookup"><span data-stu-id="f35f6-103">Gets a value indicating whether the specified metadata token has been marked as processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f35f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f35f6-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTokenMarked (  
    [in]  mdToken  tk,
    [out] BOOL     *pIsMarked  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f35f6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f35f6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="f35f6-106">podczas Token do sprawdzenia pod kątem znacznika przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f35f6-106">[in] The token to examine for a processing mark.</span></span>  
  
 `pIsMarked`  
 <span data-ttu-id="f35f6-107">określoną Wartość, która jest w `true` przypadku `tk` przetworzenia; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="f35f6-107">[out] A value that is `true` if `tk` has been processed; otherwise `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f35f6-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f35f6-108">Requirements</span></span>  
 <span data-ttu-id="f35f6-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f35f6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f35f6-110">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f35f6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f35f6-111">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f35f6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f35f6-112">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f35f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f35f6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f35f6-113">See also</span></span>

- [<span data-ttu-id="f35f6-114">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f35f6-114">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
