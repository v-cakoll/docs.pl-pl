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
ms.openlocfilehash: b10ec088f087c45b8a75805e326bc543bb64b3d9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665087"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="c8e78-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="c8e78-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="c8e78-103">Pobiera obiekt, który zezwala hostów do określenia konfiguracji wywołania zwrotnego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c8e78-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8e78-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8e78-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8e78-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="c8e78-106">[out] Wskaźnik na adres [icorconfiguration —](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiekt, który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c8e78-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8e78-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8e78-107">Remarks</span></span>  
 <span data-ttu-id="c8e78-108">Środowisko CLR musi być skonfigurowany przed inicjacji; w przeciwnym razie `GetConfiguration` metoda zwraca wartość HRESULT wskazująca na wystąpienie błędu.</span><span class="sxs-lookup"><span data-stu-id="c8e78-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8e78-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8e78-109">Requirements</span></span>  
 <span data-ttu-id="c8e78-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8e78-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8e78-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8e78-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8e78-112">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8e78-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8e78-113">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="c8e78-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e78-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c8e78-114">See also</span></span>
- [<span data-ttu-id="c8e78-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="c8e78-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
