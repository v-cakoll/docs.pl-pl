---
title: "LockClrVersion — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a58d7e99f545026f6f133901ef35a1f9b9fabc7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lockclrversion-function"></a><span data-ttu-id="24d56-102">LockClrVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="24d56-102">LockClrVersion Function</span></span>
<span data-ttu-id="24d56-103">Umożliwia hosta określić, która wersja środowisko uruchomieniowe języka wspólnego (CLR) będzie używany w ramach procesu przed jawnie inicjowania CLR.</span><span class="sxs-lookup"><span data-stu-id="24d56-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="24d56-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="24d56-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24d56-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="24d56-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24d56-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="24d56-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="24d56-107">[in] Funkcja wywoływana przez środowisko CLR po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="24d56-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="24d56-108">[in] Funkcja wywoływana przez hosta CLR informują tego inicjowania jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="24d56-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="24d56-109">[in] Funkcja wywoływana przez hosta CLR informują tego inicjowania jest ukończona.</span><span class="sxs-lookup"><span data-stu-id="24d56-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24d56-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24d56-110">Return Value</span></span>  
 <span data-ttu-id="24d56-111">Ta metoda zwraca standardowe kody błędów COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="24d56-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="24d56-112">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="24d56-112">Return code</span></span>|<span data-ttu-id="24d56-113">Opis</span><span class="sxs-lookup"><span data-stu-id="24d56-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="24d56-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="24d56-114">S_OK</span></span>|<span data-ttu-id="24d56-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="24d56-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="24d56-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="24d56-116">E_INVALIDARG</span></span>|<span data-ttu-id="24d56-117">Co najmniej jeden z argumentów ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="24d56-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24d56-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24d56-118">Remarks</span></span>  
 <span data-ttu-id="24d56-119">Wywołania hosta `LockClrVersion` przed inicjowania CLR.</span><span class="sxs-lookup"><span data-stu-id="24d56-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="24d56-120">`LockClrVersion`przyjmuje trzy parametry, które są wywołania zwrotne typu [flockclrversioncallback —](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="24d56-121">Ten typ jest zdefiniowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="24d56-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="24d56-122">Po zainicjowaniu środowiska uruchomieniowego są wykonywane następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="24d56-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="24d56-123">Wywołania hosta [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jednego z innych funkcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="24d56-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="24d56-124">Alternatywnie hosta można zainicjować za pomocą aktywacji obiektu COM środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="24d56-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="24d56-125">Środowisko uruchomieniowe wywołania funkcji określonej przez `hostCallback` parametru.</span><span class="sxs-lookup"><span data-stu-id="24d56-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="24d56-126">Funkcji określonej przez `hostCallback` następnie sprawia, że następująca sekwencja wywołania:</span><span class="sxs-lookup"><span data-stu-id="24d56-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="24d56-127">Funkcji określonej przez `pBeginHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="24d56-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="24d56-128">`CorBindToRuntimeEx`(lub inną funkcję inicjowania środowiska uruchomieniowego).</span><span class="sxs-lookup"><span data-stu-id="24d56-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="24d56-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="24d56-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="24d56-131">Funkcji określonej przez `pEndHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="24d56-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="24d56-132">Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` musi występować w jednym wątku lub włókna, z tym samym stosie logiczne.</span><span class="sxs-lookup"><span data-stu-id="24d56-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="24d56-133">Ten wątek może być inny niż wątek, na którym `hostCallback` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="24d56-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24d56-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24d56-134">Requirements</span></span>  
 <span data-ttu-id="24d56-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24d56-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24d56-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24d56-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24d56-137">**Biblioteka:** biblioteki MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24d56-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24d56-138">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24d56-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24d56-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24d56-139">See Also</span></span>  
 [<span data-ttu-id="24d56-140">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="24d56-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
