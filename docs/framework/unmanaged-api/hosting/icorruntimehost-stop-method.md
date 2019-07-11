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
ms.openlocfilehash: b1af01559e65bd80fc62cb2eba44bf21d4fa3113
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67770908"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="a7b1b-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7b1b-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a7b1b-103">Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7b1b-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a7b1b-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7b1b-105">Return Value</span></span>  
  
|<span data-ttu-id="a7b1b-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7b1b-106">HRESULT</span></span>|<span data-ttu-id="a7b1b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a7b1b-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7b1b-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7b1b-108">S_OK</span></span>|<span data-ttu-id="a7b1b-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-109">The operation was successful.</span></span>|  
|<span data-ttu-id="a7b1b-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a7b1b-110">S_FALSE</span></span>|<span data-ttu-id="a7b1b-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a7b1b-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7b1b-112">E_FAIL</span></span>|<span data-ttu-id="a7b1b-113">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a7b1b-114">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a7b1b-115">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7b1b-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7b1b-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7b1b-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7b1b-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7b1b-118">Remarks</span></span>  
 <span data-ttu-id="a7b1b-119">Nie jest to zazwyczaj konieczne do wywołania `Stop` metody, ponieważ kod zatrzymuje wykonywanie, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7b1b-120">Po wywołaniu `Stop`, środowisko CLR nie można ponownie zainicjować do tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="a7b1b-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b1b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7b1b-121">Requirements</span></span>  
 <span data-ttu-id="a7b1b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7b1b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7b1b-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7b1b-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7b1b-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7b1b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7b1b-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a7b1b-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b1b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7b1b-126">See also</span></span>

- [<span data-ttu-id="a7b1b-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7b1b-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
