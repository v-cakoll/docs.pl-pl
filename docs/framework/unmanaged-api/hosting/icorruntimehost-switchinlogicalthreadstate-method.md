---
title: ICorRuntimeHost::SwitchInLogicalThreadState — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchInLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchInLogicalThreadState method [.NET Framework hosting]
- SwitchInLogicalThreadState method [.NET Framework hosting]
ms.assetid: 7df1e492-8014-43ea-80d1-a4743e9b1c17
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d12555fb53a6c1b21f161402da77860adcf0a4b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478911"
---
# <a name="icorruntimehostswitchinlogicalthreadstate-method"></a><span data-ttu-id="16b4e-102">ICorRuntimeHost::SwitchInLogicalThreadState — Metoda</span><span class="sxs-lookup"><span data-stu-id="16b4e-102">ICorRuntimeHost::SwitchInLogicalThreadState Method</span></span>
<span data-ttu-id="16b4e-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="16b4e-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16b4e-104">Syntax</span></span>  
  
```  
HRESULT SwitchInLogicalThreadState(  
    [in] DWORD *pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16b4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16b4e-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="16b4e-106">[in] Plik cookie wskazuje fiber do użycia.</span><span class="sxs-lookup"><span data-stu-id="16b4e-106">[in] Cookie that indicates the fiber to use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16b4e-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16b4e-107">Requirements</span></span>  
 <span data-ttu-id="16b4e-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16b4e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16b4e-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="16b4e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="16b4e-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="16b4e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16b4e-111">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="16b4e-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16b4e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16b4e-112">See also</span></span>
- [<span data-ttu-id="16b4e-113">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="16b4e-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
