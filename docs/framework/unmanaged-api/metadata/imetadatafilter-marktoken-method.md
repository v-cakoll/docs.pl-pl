---
title: IMetaDataFilter::MarkToken — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataFilter::MarkToken
helpviewer_keywords:
- IMetaDataFilter::MarkToken method [.NET Framework metadata]
- MarkToken method, IMetaDataFilter interface [.NET Framework metadata]
ms.assetid: bd492834-6529-4d39-b93d-f8cdbd3e297f
topic_type:
- apiref
ms.openlocfilehash: 28a5f79f6fa8d25fd254c4093b0f76e0308edbad
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492528"
---
# <a name="imetadatafiltermarktoken-method"></a><span data-ttu-id="56a9c-102">IMetaDataFilter::MarkToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="56a9c-102">IMetaDataFilter::MarkToken Method</span></span>
<span data-ttu-id="56a9c-103">Ustawia wartość wskazującą, że określony token metadanych został przetworzony.</span><span class="sxs-lookup"><span data-stu-id="56a9c-103">Sets a value indicating that the specified metadata token has been processed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56a9c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56a9c-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkToken (  
    [in] mdToken   tk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56a9c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56a9c-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="56a9c-106">podczas Token, który ma zostać oznaczony jako przetworzony.</span><span class="sxs-lookup"><span data-stu-id="56a9c-106">[in] The token to mark as processed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56a9c-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56a9c-107">Requirements</span></span>  
 <span data-ttu-id="56a9c-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56a9c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56a9c-109">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56a9c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56a9c-110">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56a9c-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56a9c-111">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56a9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a9c-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56a9c-112">See also</span></span>

- [<span data-ttu-id="56a9c-113">IMetaDataFilter — Interfejs</span><span class="sxs-lookup"><span data-stu-id="56a9c-113">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)
