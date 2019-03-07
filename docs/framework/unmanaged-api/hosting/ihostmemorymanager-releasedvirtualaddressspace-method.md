---
title: IHostMemoryManager::ReleasedVirtualAddressSpace — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.ReleasedVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::ReleasedVirtualAddressSpace
helpviewer_keywords:
- ReleasedVirtualAddressSpace method [.NET Framework hosting]
- IHostMemoryManager::ReleasedVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: d1876601-6ab9-48e1-8ebd-184af1d0cd76
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f337ece4e68c1685f7474df4b96074597e16271a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501422"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="4a8f3-102">IHostMemoryManager::ReleasedVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a8f3-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="4a8f3-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) została zakończona, użycie pamięci określonej.</span><span class="sxs-lookup"><span data-stu-id="4a8f3-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a8f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a8f3-104">Syntax</span></span>  
  
```  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a8f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a8f3-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="4a8f3-106">[in] Wskaźnik do pamięci, które mogą być wprowadzane na adres początkowy.</span><span class="sxs-lookup"><span data-stu-id="4a8f3-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a8f3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a8f3-107">Remarks</span></span>  
 <span data-ttu-id="4a8f3-108">`ReleasedVirtualAddressSpace` Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="4a8f3-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="4a8f3-109">Jest ona wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4a8f3-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a8f3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a8f3-110">Requirements</span></span>  
 <span data-ttu-id="4a8f3-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a8f3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a8f3-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4a8f3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4a8f3-113">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a8f3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a8f3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a8f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8f3-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a8f3-115">See also</span></span>
- [<span data-ttu-id="4a8f3-116">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a8f3-116">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
