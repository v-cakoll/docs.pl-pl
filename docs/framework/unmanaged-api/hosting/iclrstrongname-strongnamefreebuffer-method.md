---
title: ICLRStrongName::StrongNameFreeBuffer — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameFreeBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameFreeBuffer
helpviewer_keywords:
- StrongNameFreeBuffer method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameFreeBuffer method [.NET Framework hosting]
ms.assetid: 6148c508-bd1d-4a37-85c3-06ecb09cc857
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef8c1e96c12b554a89d012633d1e5c347dab6de4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398527"
---
# <a name="iclrstrongnamestrongnamefreebuffer-method"></a><span data-ttu-id="c415b-102">ICLRStrongName::StrongNameFreeBuffer — Metoda</span><span class="sxs-lookup"><span data-stu-id="c415b-102">ICLRStrongName::StrongNameFreeBuffer Method</span></span>
<span data-ttu-id="c415b-103">Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do metody silnej nazwy, takie jak [iclrstrongname::strongnamegetpublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [iclrstrongname::strongnametokenfrompublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), lub [ Iclrstrongname::strongnamesignaturegeneration —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span><span class="sxs-lookup"><span data-stu-id="c415b-103">Frees memory that was allocated with a previous call to a strong name method such as [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [ICLRStrongName::StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), or [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c415b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c415b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c415b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c415b-105">Parameters</span></span>  
 `pbMemory`  
 <span data-ttu-id="c415b-106">[in] Wskaźnik do pamięci, aby zwolnić.</span><span class="sxs-lookup"><span data-stu-id="c415b-106">[in] A pointer to the memory to free.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c415b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c415b-107">Return Value</span></span>  
 <span data-ttu-id="c415b-108">`S_OK` Jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT, która wskazuje błąd (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).</span><span class="sxs-lookup"><span data-stu-id="c415b-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c415b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c415b-109">Requirements</span></span>  
 <span data-ttu-id="c415b-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c415b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c415b-111">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c415b-111">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c415b-112">**Biblioteka:** dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c415b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c415b-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c415b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c415b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c415b-114">See Also</span></span>  
 [<span data-ttu-id="c415b-115">ICLRStrongName, interfejs</span><span class="sxs-lookup"><span data-stu-id="c415b-115">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
