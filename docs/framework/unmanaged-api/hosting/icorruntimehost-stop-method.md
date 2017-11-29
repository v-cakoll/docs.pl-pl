---
title: "ICorRuntimeHost::Stop — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3f6bf66065293107efae7f401a584b7342f29125
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="311de-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="311de-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="311de-103">Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="311de-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="311de-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="311de-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="311de-105">Return Value</span></span>  
  
|<span data-ttu-id="311de-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="311de-106">HRESULT</span></span>|<span data-ttu-id="311de-107">Opis</span><span class="sxs-lookup"><span data-stu-id="311de-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="311de-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="311de-108">S_OK</span></span>|<span data-ttu-id="311de-109">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="311de-109">The operation was successful.</span></span>|  
|<span data-ttu-id="311de-110">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="311de-110">S_FALSE</span></span>|<span data-ttu-id="311de-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="311de-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="311de-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="311de-112">E_FAIL</span></span>|<span data-ttu-id="311de-113">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="311de-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="311de-114">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="311de-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="311de-115">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="311de-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="311de-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="311de-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="311de-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="311de-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="311de-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="311de-118">Remarks</span></span>  
 <span data-ttu-id="311de-119">Zwykle nie trzeba wywołać `Stop` metody, ponieważ kod zatrzymuje wykonywanie, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="311de-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="311de-120">Po wywołaniu `Stop`, CLR nie można ponownie zainicjować do tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="311de-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="311de-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="311de-121">Requirements</span></span>  
 <span data-ttu-id="311de-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="311de-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="311de-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="311de-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="311de-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="311de-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="311de-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="311de-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="311de-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="311de-126">See Also</span></span>  
 [<span data-ttu-id="311de-127">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="311de-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
