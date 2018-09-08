---
title: ICLRStrongName::StrongNameHashSize — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c09832d296033b0790d3e6282763a1163abdfd2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130461"
---
# <a name="iclrstrongnamestrongnamehashsize-method"></a><span data-ttu-id="25b85-102">ICLRStrongName::StrongNameHashSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="25b85-102">ICLRStrongName::StrongNameHashSize Method</span></span>
<span data-ttu-id="25b85-103">Pobiera rozmiar bufora wymaganych do wyznaczania wartości skrótu, za pomocą określonego algorytmu skrótu.</span><span class="sxs-lookup"><span data-stu-id="25b85-103">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25b85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25b85-104">Syntax</span></span>  
  
```  
HRESULT StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25b85-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25b85-105">Parameters</span></span>  
 `ulHashAlg`  
 <span data-ttu-id="25b85-106">[in] Algorytm wyznaczania wartości skrótu używany do obliczania rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="25b85-106">[in] The hash algorithm used to compute the buffer size.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="25b85-107">[out] Rozmiar buforu zwrócony w bajtach.</span><span class="sxs-lookup"><span data-stu-id="25b85-107">[out] The returned buffer size, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25b85-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25b85-108">Return Value</span></span>  
 <span data-ttu-id="25b85-109">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="25b85-109">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25b85-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25b85-110">Requirements</span></span>  
 <span data-ttu-id="25b85-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b85-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b85-112">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="25b85-112">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="25b85-113">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25b85-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25b85-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b85-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b85-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25b85-115">See Also</span></span>  
 [<span data-ttu-id="25b85-116">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="25b85-116">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
