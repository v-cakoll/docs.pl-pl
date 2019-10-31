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
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139565"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="9aab2-102">ICorRuntimeHost::GetConfiguration — Metoda</span><span class="sxs-lookup"><span data-stu-id="9aab2-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="9aab2-103">Pobiera obiekt, który umożliwia hostowi określenie konfiguracji wywołania zwrotnego środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9aab2-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9aab2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9aab2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9aab2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9aab2-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="9aab2-106">określoną Wskaźnik do adresu obiektu [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) , który może służyć do konfigurowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="9aab2-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9aab2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9aab2-107">Remarks</span></span>  
 <span data-ttu-id="9aab2-108">Środowisko CLR musi być skonfigurowane przed jego inicjalizacją; w przeciwnym razie metoda `GetConfiguration` zwraca wartość HRESULT wskazującą błąd.</span><span class="sxs-lookup"><span data-stu-id="9aab2-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9aab2-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9aab2-109">Requirements</span></span>  
 <span data-ttu-id="9aab2-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9aab2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9aab2-111">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9aab2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9aab2-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9aab2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9aab2-113">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9aab2-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aab2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9aab2-114">See also</span></span>

- [<span data-ttu-id="9aab2-115">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="9aab2-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
