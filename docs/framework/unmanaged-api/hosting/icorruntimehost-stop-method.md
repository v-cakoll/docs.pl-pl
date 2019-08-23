---
title: ICorRuntimeHost::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca51b87e7afc8e9e48d541a32b3bd60a19a5ff70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965967"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="ea8be-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea8be-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="ea8be-103">Kończy wykonywanie kodu w środowisku uruchomieniowym dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="ea8be-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea8be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea8be-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ea8be-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ea8be-105">Return Value</span></span>  
  
|<span data-ttu-id="ea8be-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ea8be-106">HRESULT</span></span>|<span data-ttu-id="ea8be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ea8be-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea8be-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="ea8be-108">S_OK</span></span>|<span data-ttu-id="ea8be-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ea8be-109">The operation was successful.</span></span>|  
|<span data-ttu-id="ea8be-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ea8be-110">S_FALSE</span></span>|<span data-ttu-id="ea8be-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="ea8be-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ea8be-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ea8be-112">E_FAIL</span></span>|<span data-ttu-id="ea8be-113">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="ea8be-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ea8be-114">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="ea8be-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ea8be-115">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ea8be-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ea8be-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ea8be-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ea8be-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ea8be-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea8be-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea8be-118">Remarks</span></span>  
 <span data-ttu-id="ea8be-119">Zazwyczaj nie jest konieczne wywoływanie `Stop` metody, ponieważ kod kończy wykonywanie po zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="ea8be-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea8be-120">Po wywołaniu `Stop`, nie można ponownie zainicjować środowiska CLR w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="ea8be-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea8be-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea8be-121">Requirements</span></span>  
 <span data-ttu-id="ea8be-122">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea8be-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea8be-123">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ea8be-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ea8be-124">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ea8be-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ea8be-125">**.NET Framework wersje:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ea8be-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8be-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea8be-126">See also</span></span>

- [<span data-ttu-id="ea8be-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="ea8be-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
