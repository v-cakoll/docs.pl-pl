---
title: ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.SwitchOutLogicalThreadState
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1291d4e69843db7bd90af07291da415220d98807
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131361"
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="0f93a-102">ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f93a-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="0f93a-103">Ta metoda obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="0f93a-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f93a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f93a-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f93a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f93a-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="0f93a-106">[out] Plik cookie wskazuje fiber przełączany.</span><span class="sxs-lookup"><span data-stu-id="0f93a-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f93a-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f93a-107">Requirements</span></span>  
 <span data-ttu-id="0f93a-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f93a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f93a-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f93a-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f93a-110">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f93a-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f93a-111">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="0f93a-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f93a-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f93a-112">See also</span></span>

- [<span data-ttu-id="0f93a-113">ICorRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0f93a-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
