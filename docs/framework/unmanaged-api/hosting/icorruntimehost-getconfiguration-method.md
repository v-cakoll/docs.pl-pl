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
ms.openlocfilehash: 3c51ddae6aa62552bac9990b57a173c28f73bae5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436835"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="62458-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="62458-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="62458-103">Pobiera obiekt, który umożliwia hosta określić konfigurację wywołania zwrotnego środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="62458-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62458-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62458-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62458-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62458-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="62458-106">[out] Wskaźnik do adresu [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiektu, który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="62458-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62458-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62458-107">Remarks</span></span>  
 <span data-ttu-id="62458-108">Przed jego inicjowania; należy skonfigurować środowisko CLR w przeciwnym razie `GetConfiguration` metoda zwróci wartość HRESULT wskazujący błąd.</span><span class="sxs-lookup"><span data-stu-id="62458-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62458-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62458-109">Requirements</span></span>  
 <span data-ttu-id="62458-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62458-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62458-111">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="62458-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="62458-112">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="62458-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="62458-113">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="62458-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62458-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62458-114">See Also</span></span>  
 [<span data-ttu-id="62458-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="62458-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
