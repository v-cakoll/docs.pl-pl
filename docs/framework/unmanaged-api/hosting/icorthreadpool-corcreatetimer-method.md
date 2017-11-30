---
title: "ICorThreadpool::CorCreateTimer — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorCreateTimer
api_location: mscoree.dll
api_type: COM
f1_keywords: CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 70a7c389ac44e8a513ec8a764d19c9a316ca7c08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="48943-102">ICorThreadpool::CorCreateTimer — Metoda</span><span class="sxs-lookup"><span data-stu-id="48943-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="48943-103">Ta metoda obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="48943-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48943-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48943-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="48943-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48943-105">Requirements</span></span>  
 <span data-ttu-id="48943-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48943-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48943-107">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="48943-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="48943-108">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="48943-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="48943-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48943-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48943-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48943-110">See Also</span></span>  
 [<span data-ttu-id="48943-111">ICorThreadpool — interfejs</span><span class="sxs-lookup"><span data-stu-id="48943-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
