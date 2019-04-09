---
title: ITypeName::GetTypeArguments — Metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArguments
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArguments
helpviewer_keywords:
- ITypeName::GetTypeArguments method [.NET Framework hosting]
- GetTypeArguments method [.NET Framework hosting]
ms.assetid: 638d77df-ff9c-40d9-88ee-930f5f87ada1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cd4fa8f4ba2bea5a2a853544eae6239bfaaeba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132278"
---
# <a name="itypenamegettypearguments-method"></a><span data-ttu-id="f0043-102">ITypeName::GetTypeArguments — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0043-102">ITypeName::GetTypeArguments Method</span></span>
<span data-ttu-id="f0043-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f0043-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0043-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0043-104">Syntax</span></span>  
  
```  
HRESULT GetTypeArguments (  
    [in] DWORD           count,  
    [out] ITypeName**    rgpArguments,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f0043-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0043-105">Requirements</span></span>  
 <span data-ttu-id="f0043-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0043-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0043-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f0043-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f0043-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f0043-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="f0043-109">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f0043-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0043-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0043-110">See also</span></span>

- [<span data-ttu-id="f0043-111">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0043-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
