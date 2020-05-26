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
ms.openlocfilehash: 4a246fb95ab5b4a7f187aa660f20e590c63ddff2
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804468"
---
# <a name="ihostmemorymanagerreleasedvirtualaddressspace-method"></a><span data-ttu-id="52ec3-102">IHostMemoryManager::ReleasedVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="52ec3-102">IHostMemoryManager::ReleasedVirtualAddressSpace Method</span></span>
<span data-ttu-id="52ec3-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) zostało zakończone przy użyciu określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="52ec3-103">Notifies the host that the common language runtime (CLR) has finished using the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52ec3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52ec3-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleasedVirtualAddressSpace(  
    [in] LPVOID startAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52ec3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="52ec3-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="52ec3-106">podczas Wskaźnik na adres początkowy pamięci, która ma zostać wydana.</span><span class="sxs-lookup"><span data-stu-id="52ec3-106">[in] Pointer to the starting address of the memory to be released.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52ec3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52ec3-107">Remarks</span></span>  
 <span data-ttu-id="52ec3-108">`ReleasedVirtualAddressSpace`Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="52ec3-108">The `ReleasedVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="52ec3-109">Jest wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="52ec3-109">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52ec3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52ec3-110">Requirements</span></span>  
 <span data-ttu-id="52ec3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52ec3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52ec3-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="52ec3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="52ec3-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="52ec3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="52ec3-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52ec3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52ec3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52ec3-115">See also</span></span>

- [<span data-ttu-id="52ec3-116">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="52ec3-116">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
