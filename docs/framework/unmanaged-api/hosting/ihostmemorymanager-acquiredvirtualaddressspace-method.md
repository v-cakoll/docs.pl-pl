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
ms.openlocfilehash: b70454cd1e2d6d38e6ca4d0ea0bd8974963c201c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136740"
---
# <a name="ihostmemorymanageracquiredvirtualaddressspace-method"></a><span data-ttu-id="6a641-102">IHostMemoryManager::AcquiredVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="6a641-102">IHostMemoryManager::AcquiredVirtualAddressSpace Method</span></span>
<span data-ttu-id="6a641-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) uzyskało określoną ilość pamięci z systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6a641-103">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a641-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a641-104">Syntax</span></span>  
  
```cpp  
HRESULT AcquiredVirtualAddressSpace(  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a641-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6a641-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="6a641-106">podczas Adres początkowy pamięci.</span><span class="sxs-lookup"><span data-stu-id="6a641-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="6a641-107">podczas Rozmiar pamięci (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="6a641-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a641-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a641-108">Remarks</span></span>  
 <span data-ttu-id="6a641-109">Metoda `AcquiredVirtualAddressSpace` jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="6a641-109">The `AcquiredVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="6a641-110">Jest wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="6a641-110">It is called by the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a641-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a641-111">Requirements</span></span>  
 <span data-ttu-id="6a641-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a641-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a641-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a641-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a641-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6a641-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a641-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a641-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a641-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a641-116">See also</span></span>

- [<span data-ttu-id="6a641-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="6a641-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
