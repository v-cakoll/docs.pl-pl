---
title: IObjectHandle::Unwrap — Metoda
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
ms.openlocfilehash: 0ff088731514b2da0d8b1fa51ef48d8b71d16528
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842234"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="9f245-102">IObjectHandle::Unwrap — Metoda</span><span class="sxs-lookup"><span data-stu-id="9f245-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="9f245-103">Odpakuje obiekt zorganizowany przez wartość z pośredniego.</span><span class="sxs-lookup"><span data-stu-id="9f245-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f245-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9f245-104">Syntax</span></span>  
  
```cpp  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f245-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f245-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="9f245-106">określoną Wskaźnik do obiektu, który ma zostać rozpakowany.</span><span class="sxs-lookup"><span data-stu-id="9f245-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f245-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9f245-107">Requirements</span></span>  
 <span data-ttu-id="9f245-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f245-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f245-109">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9f245-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f245-110">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f245-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f245-111">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f245-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
