---
title: IHostSecurityContext — Interfejs
ms.date: 03/30/2017
api_name:
- IHostSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityContext
helpviewer_keywords:
- IHostSecurityContext interface [.NET Framework hosting]
ms.assetid: 88e2eac0-8ccb-404f-abbc-287d55159842
topic_type:
- apiref
ms.openlocfilehash: f6e25bfe11880730f6f447ccc0406d716d185624
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501498"
---
# <a name="ihostsecuritycontext-interface"></a><span data-ttu-id="8d76e-102">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8d76e-102">IHostSecurityContext Interface</span></span>
<span data-ttu-id="8d76e-103">Umożliwia środowisko uruchomieniowe języka wspólnego (CLR), aby zachować informacje kontekstu zabezpieczeń zaimplementowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="8d76e-103">Allows the common language runtime (CLR) to maintain security context information implemented by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d76e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8d76e-104">Methods</span></span>  
  
|<span data-ttu-id="8d76e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d76e-105">Method</span></span>|<span data-ttu-id="8d76e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8d76e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d76e-107">Capture, metoda</span><span class="sxs-lookup"><span data-stu-id="8d76e-107">Capture Method</span></span>](ihostsecuritycontext-capture-method.md)|<span data-ttu-id="8d76e-108">Pobiera klon `IHostSecurityContext` wystąpienia zwróconego z wywołania do [IHostSecurityManager:: GetSecurityContext —](ihostsecuritymanager-getsecuritycontext-method.md).</span><span class="sxs-lookup"><span data-stu-id="8d76e-108">Gets a clone of the `IHostSecurityContext` instance returned from a call to [IHostSecurityManager::GetSecurityContext](ihostsecuritymanager-getsecuritycontext-method.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d76e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d76e-109">Remarks</span></span>  
 <span data-ttu-id="8d76e-110">Host może kontrolować cały dostęp kodu do tokenów wątków przez środowisko CLR i kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8d76e-110">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="8d76e-111">Może także zapewnić, że pełne informacje kontekstu zabezpieczeń są przesyłane przez operacje asynchroniczne lub punkty kodowe z ograniczonym dostępem do kodu.</span><span class="sxs-lookup"><span data-stu-id="8d76e-111">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="8d76e-112">`IHostSecurityContext`hermetyzuje informacje kontekstu zabezpieczeń, które są nieprzezroczyste dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="8d76e-112">`IHostSecurityContext` encapsulates this security context information, which is opaque to the runtime.</span></span> <span data-ttu-id="8d76e-113">Środowisko uruchomieniowe przechwytuje te informacje przy użyciu `Capture` i przenosi je między elementami roboczymi puli wątków, wykonywaniem finalizatora oraz konstruktorami modułów i klas.</span><span class="sxs-lookup"><span data-stu-id="8d76e-113">The runtime captures this information using `Capture`, and moves it across thread pool worker item dispatch, finalizer execution, and module and class constructors.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d76e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d76e-114">Requirements</span></span>  
 <span data-ttu-id="8d76e-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d76e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d76e-116">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8d76e-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8d76e-117">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8d76e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8d76e-118">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d76e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d76e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d76e-119">See also</span></span>

- [<span data-ttu-id="8d76e-120">ICLRHostProtectionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d76e-120">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="8d76e-121">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d76e-121">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
- [<span data-ttu-id="8d76e-122">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8d76e-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
