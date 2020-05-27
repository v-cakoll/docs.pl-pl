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
ms.openlocfilehash: bb13c7329c558aa92ec65237aa8a9963c82fe1dc
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804511"
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="df325-102">IHostMemoryManager::NeedsVirtualAddressSpace — Metoda</span><span class="sxs-lookup"><span data-stu-id="df325-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="df325-103">Powiadamia hosta, że środowisko uruchomieniowe języka wspólnego (CLR) próbuje użyć określonej pamięci.</span><span class="sxs-lookup"><span data-stu-id="df325-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df325-104">Syntax</span></span>  
  
```cpp  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df325-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df325-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="df325-106">podczas Adres początkowy pamięci.</span><span class="sxs-lookup"><span data-stu-id="df325-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="df325-107">podczas Rozmiar pamięci (w bajtach).</span><span class="sxs-lookup"><span data-stu-id="df325-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df325-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df325-108">Remarks</span></span>  
 <span data-ttu-id="df325-109">`NeedsVirtualAddressSpace`Metoda jest metodą wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="df325-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="df325-110">Jest wywoływana przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="df325-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="df325-111">Jeśli host nie chce, aby środowisko CLR używało określonej pamięci, może zwrócić E_OUTOFMEMORY HRESULT.</span><span class="sxs-lookup"><span data-stu-id="df325-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df325-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df325-112">Requirements</span></span>  
 <span data-ttu-id="df325-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df325-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df325-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="df325-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df325-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="df325-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df325-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df325-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df325-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df325-117">See also</span></span>

- [<span data-ttu-id="df325-118">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="df325-118">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
