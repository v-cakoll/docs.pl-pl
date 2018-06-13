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
ms.openlocfilehash: 87c97a678fce4c25a113670a4668515a898e5251
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438421"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="b85d3-102">IHostMemoryManager::NeedsVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="b85d3-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="b85d3-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) ma próbować używać pamięci określony.</span><span class="sxs-lookup"><span data-stu-id="b85d3-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b85d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b85d3-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b85d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b85d3-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="b85d3-106">[in] Początkowy adres pamięci.</span><span class="sxs-lookup"><span data-stu-id="b85d3-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="b85d3-107">[in] Rozmiar w bajtach pamięci.</span><span class="sxs-lookup"><span data-stu-id="b85d3-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b85d3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b85d3-108">Remarks</span></span>  
 <span data-ttu-id="b85d3-109">`NeedsVirtualAddressSpace` Metoda to metoda wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b85d3-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="b85d3-110">Jest ona wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="b85d3-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="b85d3-111">Jeśli host nie chce CLR do użycia pamięci określony, zwracać E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b85d3-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b85d3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b85d3-112">Requirements</span></span>  
 <span data-ttu-id="b85d3-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b85d3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b85d3-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b85d3-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b85d3-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b85d3-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b85d3-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b85d3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b85d3-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b85d3-117">See Also</span></span>  
 [<span data-ttu-id="b85d3-118">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b85d3-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
