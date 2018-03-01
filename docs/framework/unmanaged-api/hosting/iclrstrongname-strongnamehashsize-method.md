---
title: "ICLRStrongName::StrongNameHashSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRStrongName.StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameHashSize
helpviewer_keywords:
- ICLRStrongName::StrongNameHashSize method [.NET Framework hosting]
- StrongNameHashSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 4a05ee56-08e4-4f3a-86a9-9b52083d5c0f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: acc2812567ce2d47d3f06c000fc387708c2e8acb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="6bce3-102">ICLRStrongName::StrongNameHashSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="6bce3-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="6bce3-103">Pobiera wymagane dla skrótu, przy użyciu algorytmu wyznaczania wartości skrótu określonej rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bce3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bce3-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bce3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bce3-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="6bce3-106">[in] Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="6bce3-107">[out] Rozmiar buforu zwrócony w bajtach.</span><span class="sxs-lookup"><span data-stu-id="6bce3-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bce3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6bce3-108">Return Value</span></span>  
 <span data-ttu-id="6bce3-109">`S_OK`Jeśli metoda zakończyła się pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje niepowodzenie (zobacz [wspólne wartości HRESULT](http://go.microsoft.com/fwlink/?LinkId=213878) lista).</span><span class="sxs-lookup"><span data-stu-id="6bce3-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bce3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bce3-110">Requirements</span></span>  
 <span data-ttu-id="6bce3-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bce3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bce3-112">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6bce3-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6bce3-113">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6bce3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bce3-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bce3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bce3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bce3-115">See Also</span></span>  
 [<span data-ttu-id="6bce3-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="6bce3-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
