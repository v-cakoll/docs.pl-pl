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
ms.openlocfilehash: 4117c1297f02032fda80520a7709833217ec94b1
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762698"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="2fa1f-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="2fa1f-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="2fa1f-103">Kończy wykonywanie kodu w środowisku uruchomieniowym dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2fa1f-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2fa1f-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2fa1f-105">Return Value</span></span>  
  
|<span data-ttu-id="2fa1f-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fa1f-106">HRESULT</span></span>|<span data-ttu-id="2fa1f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2fa1f-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fa1f-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fa1f-108">S_OK</span></span>|<span data-ttu-id="2fa1f-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-109">The operation was successful.</span></span>|  
|<span data-ttu-id="2fa1f-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2fa1f-110">S_FALSE</span></span>|<span data-ttu-id="2fa1f-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2fa1f-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fa1f-112">E_FAIL</span></span>|<span data-ttu-id="2fa1f-113">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2fa1f-114">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2fa1f-115">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2fa1f-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2fa1f-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2fa1f-117">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa1f-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2fa1f-118">Remarks</span></span>  
 <span data-ttu-id="2fa1f-119">Zazwyczaj nie jest konieczne wywoływanie `Stop` metody, ponieważ kod kończy wykonywanie po zakończeniu procesu.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fa1f-120">Po wywołaniu `Stop` , nie można ponownie zainicjować środowiska CLR w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="2fa1f-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa1f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2fa1f-121">Requirements</span></span>  
 <span data-ttu-id="2fa1f-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa1f-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa1f-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2fa1f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fa1f-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2fa1f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fa1f-125">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2fa1f-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa1f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2fa1f-126">See also</span></span>

- [<span data-ttu-id="2fa1f-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="2fa1f-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
