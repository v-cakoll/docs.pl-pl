---
title: "IHostMemoryManager::ReleasedVirtualAddressSpace — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.ReleasedVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c0f2588c34429366794fcfb30c6d6e7038814506
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="86890-102">IHostMemoryManager::ReleasedVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="86890-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="86890-103">Powiadamia hosta środowisko uruchomieniowe języka wspólnego (CLR) zostało zakończone, przy użyciu określonego pamięci.</span><span class="sxs-lookup"><span data-stu-id="86890-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86890-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86890-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="86890-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86890-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="86890-106">[in] Wskaźnik do początkowy adres pamięci do zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="86890-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86890-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86890-107">Remarks</span></span>  
 <span data-ttu-id="86890-108">`ReleasedVirtualAddressSpace` Metoda to metoda wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86890-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="86890-109">Jest ona wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="86890-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86890-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86890-110">Requirements</span></span>  
 <span data-ttu-id="86890-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86890-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86890-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="86890-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="86890-113">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="86890-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="86890-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86890-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86890-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="86890-115">See Also</span></span>  
 [<span data-ttu-id="86890-116">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="86890-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
