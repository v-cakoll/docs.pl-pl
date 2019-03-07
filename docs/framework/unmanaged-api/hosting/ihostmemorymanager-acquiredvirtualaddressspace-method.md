---
title: IHostMemoryManager::AcquiredVirtualAddressSpace — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.AcquiredVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::AcquiredVirtualAddressSpace method [.NET Framework hosting]
- AcquiredVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: ef2f83c2-127e-4c38-8385-306c03cd2167
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67fc415f1569abd35819d7b3a59459052e3591ba
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486137"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="ac549-102">IHostMemoryManager::AcquiredVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="ac549-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="ac549-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskała określonego pamięci systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ac549-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac549-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac549-104">Syntax</span></span>  
  
```  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac549-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ac549-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="ac549-106">[in] Początkowy adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="ac549-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="ac549-107">[in] Rozmiar w bajtach pamięci.</span><span class="sxs-lookup"><span data-stu-id="ac549-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac549-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac549-108">Remarks</span></span>  
 <span data-ttu-id="ac549-109">`AcquiredVirtualAddressSpace` Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="ac549-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="ac549-110">Jest ona wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="ac549-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac549-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ac549-111">Requirements</span></span>  
 <span data-ttu-id="ac549-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac549-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac549-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ac549-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac549-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ac549-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac549-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac549-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac549-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac549-116">See also</span></span>
- [<span data-ttu-id="ac549-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ac549-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
