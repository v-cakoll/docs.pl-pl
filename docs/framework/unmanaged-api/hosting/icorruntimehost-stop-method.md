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
ms.openlocfilehash: 3ef92fbe5ba99d93eaf06aacc7efd943136e9785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543201"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="6b91a-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b91a-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="6b91a-103">Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="6b91a-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b91a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b91a-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="6b91a-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6b91a-105">Return Value</span></span>  
  
|<span data-ttu-id="6b91a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6b91a-106">HRESULT</span></span>|<span data-ttu-id="6b91a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6b91a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6b91a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b91a-108">S_OK</span></span>|<span data-ttu-id="6b91a-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="6b91a-109">The operation was successful.</span></span>|  
|<span data-ttu-id="6b91a-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6b91a-110">S_FALSE</span></span>|<span data-ttu-id="6b91a-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="6b91a-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6b91a-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6b91a-112">E_FAIL</span></span>|<span data-ttu-id="6b91a-113">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="6b91a-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6b91a-114">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="6b91a-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6b91a-115">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6b91a-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6b91a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6b91a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6b91a-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6b91a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b91a-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b91a-118">Remarks</span></span>  
 <span data-ttu-id="6b91a-119">Nie jest to zazwyczaj konieczne do wywołania `Stop` metody, ponieważ kod zatrzymuje wykonywanie, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="6b91a-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b91a-120">Po wywołaniu `Stop`, środowisko CLR nie można ponownie zainicjować do tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="6b91a-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b91a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b91a-121">Requirements</span></span>  
 <span data-ttu-id="6b91a-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b91a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b91a-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b91a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b91a-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6b91a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b91a-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6b91a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b91a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b91a-126">See also</span></span>
- [<span data-ttu-id="6b91a-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6b91a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
