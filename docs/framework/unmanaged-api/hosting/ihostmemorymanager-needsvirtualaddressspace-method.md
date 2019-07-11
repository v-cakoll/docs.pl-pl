---
title: IHostMemoryManager::NeedsVirtualAddressSpace — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.NeedsVirtualAddressSpace
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57ed64ad8a6ae8ef46f423471436c3fce29d6fe5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767806"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="4d4c9-102">IHostMemoryManager::NeedsVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d4c9-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="4d4c9-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma podejmują próbę użycia określonego pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d4c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d4c9-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d4c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d4c9-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="4d4c9-106">[in] Początkowy adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="4d4c9-107">[in] Rozmiar w bajtach pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d4c9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d4c9-108">Remarks</span></span>  
 <span data-ttu-id="4d4c9-109">`NeedsVirtualAddressSpace` Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="4d4c9-110">Jest ona wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="4d4c9-111">Jeśli host nie chce CLR, aby użyć określonego pamięci, może on zwrócić wartość HRESULT E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="4d4c9-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d4c9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d4c9-112">Requirements</span></span>  
 <span data-ttu-id="4d4c9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d4c9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d4c9-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4d4c9-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d4c9-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d4c9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d4c9-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d4c9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4c9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d4c9-117">See also</span></span>

- [<span data-ttu-id="4d4c9-118">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d4c9-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
