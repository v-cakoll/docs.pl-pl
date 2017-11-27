---
title: "ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.SwitchOutLogicalThreadState
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::SwitchOutLogicalThreadState
helpviewer_keywords:
- ICorRuntimeHost::SwitchOutLogicalThreadState method [.NET Framework hosting]
- SwitchOutLogicalThreadState method [.NET Framework hosting]
ms.assetid: e1968f0b-2675-4dc2-8507-46164e1df154
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9eed11dd0a5ebd30952946f640957e9960485524
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostswitchoutlogicalthreadstate-method"></a><span data-ttu-id="e1e48-102">ICorRuntimeHost::SwitchOutLogicalThreadState — Metoda</span><span class="sxs-lookup"><span data-stu-id="e1e48-102">ICorRuntimeHost::SwitchOutLogicalThreadState Method</span></span>
<span data-ttu-id="e1e48-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e1e48-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e48-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1e48-104">Syntax</span></span>  
  
```  
HRESULT SwitchOutLogicalThreadState(  
    [out] DWORD **pFiberCookie  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1e48-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1e48-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e1e48-106">[out] Plik cookie wskazuje fiber przełączany wychodzących.</span><span class="sxs-lookup"><span data-stu-id="e1e48-106">[out] Cookie that indicates the fiber being switched out.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1e48-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1e48-107">Requirements</span></span>  
 <span data-ttu-id="e1e48-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1e48-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1e48-109">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e1e48-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1e48-110">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e1e48-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1e48-111">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e1e48-111">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1e48-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1e48-112">See Also</span></span>  
 [<span data-ttu-id="e1e48-113">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="e1e48-113">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
