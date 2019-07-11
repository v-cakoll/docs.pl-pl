---
title: ITypeName::GetModifiers — Metoda
ms.date: 03/30/2017
api_name:
- ITypeName.GetModifiers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetModifiers
helpviewer_keywords:
- ITypeName::GetModifiers method [.NET Framework hosting]
- GetModifiers method [.NET Framework hosting]
ms.assetid: 75508c55-3e09-4135-80da-cc811003fa82
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 15804673733ffba7e65c3d280cdc87a76739aaed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748987"
---
# <a name="itypenamegetmodifiers-method"></a><span data-ttu-id="95cc5-102">ITypeName::GetModifiers — Metoda</span><span class="sxs-lookup"><span data-stu-id="95cc5-102">ITypeName::GetModifiers Method</span></span>
<span data-ttu-id="95cc5-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="95cc5-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95cc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95cc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModifiers (  
    [in] DWORD           count,  
    [out] DWORD*         rgModifiers,  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="95cc5-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95cc5-105">Requirements</span></span>  
 <span data-ttu-id="95cc5-106">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95cc5-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95cc5-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="95cc5-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95cc5-108">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95cc5-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95cc5-109">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95cc5-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95cc5-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95cc5-110">See also</span></span>

- [<span data-ttu-id="95cc5-111">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="95cc5-111">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
