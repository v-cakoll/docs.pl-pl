---
title: ICorRuntimeHost::GetConfiguration — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf74da6eb0e7ce0215023a9a58d6b88c57c4fe8b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097340"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="07c2a-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="07c2a-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="07c2a-103">Pobiera obiekt, który zezwala hostów do określenia konfiguracji wywołania zwrotnego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="07c2a-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07c2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07c2a-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07c2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="07c2a-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="07c2a-106">[out] Wskaźnik na adres [icorconfiguration —](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiekt, który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="07c2a-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07c2a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07c2a-107">Remarks</span></span>  
 <span data-ttu-id="07c2a-108">Środowisko CLR musi być skonfigurowany przed inicjacji; w przeciwnym razie `GetConfiguration` metoda zwraca wartość HRESULT wskazująca na wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="07c2a-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07c2a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07c2a-109">Requirements</span></span>  
 <span data-ttu-id="07c2a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07c2a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07c2a-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="07c2a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="07c2a-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="07c2a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="07c2a-113">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="07c2a-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07c2a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07c2a-114">See also</span></span>

- [<span data-ttu-id="07c2a-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="07c2a-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
