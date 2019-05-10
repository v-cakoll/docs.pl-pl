---
title: LockClrVersion — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3a2a367f6af1deeb1201d391af271a4bd45ac
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584994"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="d99a6-102">LockClrVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="d99a6-102">LockClrVersion Function</span></span>
<span data-ttu-id="d99a6-103">Umożliwia hostowi na określenie, która wersja środowiska uruchomieniowego języka wspólnego (CLR), będą używane w ramach procesu przed jawnym zainicjowaniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d99a6-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="d99a6-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d99a6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d99a6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d99a6-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d99a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d99a6-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="d99a6-107">[in] Funkcja, która ma zostać wywołana przez środowisko CLR po zainicjowaniu.</span><span class="sxs-lookup"><span data-stu-id="d99a6-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="d99a6-108">[in] Funkcja wywoływana przez hosta w celu poinformowania środowiska CLR, że inicjowanie jest uruchamiana.</span><span class="sxs-lookup"><span data-stu-id="d99a6-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="d99a6-109">[in] Funkcja wywoływana przez hosta w celu poinformowania środowiska CLR, że Inicjowanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="d99a6-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d99a6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d99a6-110">Return Value</span></span>  
 <span data-ttu-id="d99a6-111">Ta metoda zwraca standardowe kody błędu modelu COM, zgodnie z definicją w pliku WinError.h oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="d99a6-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="d99a6-112">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="d99a6-112">Return code</span></span>|<span data-ttu-id="d99a6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="d99a6-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d99a6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d99a6-114">S_OK</span></span>|<span data-ttu-id="d99a6-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d99a6-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="d99a6-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="d99a6-116">E_INVALIDARG</span></span>|<span data-ttu-id="d99a6-117">Co najmniej jeden z argumentów ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d99a6-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d99a6-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d99a6-118">Remarks</span></span>  
 <span data-ttu-id="d99a6-119">Wywołania hosta `LockClrVersion` przed zainicjowaniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d99a6-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="d99a6-120">`LockClrVersion` przyjmuje trzy parametry, które są wywołania zwrotne typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="d99a6-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="d99a6-121">Ten typ jest zdefiniowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d99a6-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="d99a6-122">Po zainicjowaniu środowiska uruchomieniowego są wykonywane następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="d99a6-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="d99a6-123">Wywołania hosta [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jednego z innych funkcji inicjowania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d99a6-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="d99a6-124">Alternatywnie hosta można zainicjować aparatu plików wykonywalnych przy użyciu aktywowanie obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="d99a6-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="d99a6-125">Środowisko wykonawcze wywołuje funkcji określonej przez `hostCallback` parametru.</span><span class="sxs-lookup"><span data-stu-id="d99a6-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="d99a6-126">Funkcji określonej przez `hostCallback` następnie sprawia, że następująca sekwencja wywołań:</span><span class="sxs-lookup"><span data-stu-id="d99a6-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="d99a6-127">Funkcji określonej przez `pBeginHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="d99a6-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="d99a6-128">`CorBindToRuntimeEx` (lub inną funkcję inicjowania środowiska uruchomieniowego).</span><span class="sxs-lookup"><span data-stu-id="d99a6-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="d99a6-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="d99a6-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="d99a6-130">[Iclrruntimehost::Start —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="d99a6-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="d99a6-131">Funkcji określonej przez `pEndHostSetup` parametru.</span><span class="sxs-lookup"><span data-stu-id="d99a6-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="d99a6-132">Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` musi przypadać na jednym wątku lub włókna, z tym samym stosie logiczne.</span><span class="sxs-lookup"><span data-stu-id="d99a6-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="d99a6-133">Ten wątek może różnić się od wątku, na którym `hostCallback` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d99a6-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99a6-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d99a6-134">Requirements</span></span>  
 <span data-ttu-id="d99a6-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d99a6-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d99a6-136">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d99a6-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d99a6-137">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d99a6-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d99a6-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d99a6-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99a6-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d99a6-139">See also</span></span>

- [<span data-ttu-id="d99a6-140">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="d99a6-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
