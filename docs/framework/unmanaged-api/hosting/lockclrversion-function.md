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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133776"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="a27f0-102">LockClrVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a27f0-102">LockClrVersion Function</span></span>
<span data-ttu-id="a27f0-103">Umożliwia hostowi określenie, która wersja środowiska uruchomieniowego języka wspólnego (CLR) zostanie użyta w procesie przed jawnym inicjalizacją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a27f0-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="a27f0-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a27f0-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a27f0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a27f0-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a27f0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a27f0-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="a27f0-107">podczas Funkcja, która ma zostać wywołana przez środowisko CLR po inicjacji.</span><span class="sxs-lookup"><span data-stu-id="a27f0-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="a27f0-108">podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania o uruchamianiu CLR.</span><span class="sxs-lookup"><span data-stu-id="a27f0-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="a27f0-109">podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania środowiska CLR o ukończeniu inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="a27f0-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a27f0-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a27f0-110">Return Value</span></span>  
 <span data-ttu-id="a27f0-111">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="a27f0-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a27f0-112">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a27f0-112">Return code</span></span>|<span data-ttu-id="a27f0-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a27f0-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a27f0-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a27f0-114">S_OK</span></span>|<span data-ttu-id="a27f0-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a27f0-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="a27f0-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a27f0-116">E_INVALIDARG</span></span>|<span data-ttu-id="a27f0-117">Co najmniej jeden argument ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a27f0-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a27f0-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a27f0-118">Remarks</span></span>  
 <span data-ttu-id="a27f0-119">Host wywołuje `LockClrVersion` przed zainicjowaniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a27f0-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="a27f0-120">`LockClrVersion` pobiera trzy parametry, z których wszystkie są wywołaniami zwrotnymi typu [FLockClrVersionCallback —](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="a27f0-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="a27f0-121">Ten typ jest definiowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a27f0-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="a27f0-122">Następujące kroki są wykonywane po zainicjowaniu środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="a27f0-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="a27f0-123">Host wywołuje [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub jedną z innych funkcji inicjalizacji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a27f0-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="a27f0-124">Alternatywnie host może zainicjować środowisko uruchomieniowe przy użyciu funkcji aktywacji obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="a27f0-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="a27f0-125">Środowisko uruchomieniowe wywołuje funkcję określoną przez parametr `hostCallback`.</span><span class="sxs-lookup"><span data-stu-id="a27f0-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="a27f0-126">Funkcja określona przez `hostCallback` następnie wykonuje następującą sekwencję wywołań:</span><span class="sxs-lookup"><span data-stu-id="a27f0-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="a27f0-127">Funkcja określona przez parametr `pBeginHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="a27f0-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="a27f0-128">`CorBindToRuntimeEx` (lub inna funkcja inicjacji środowiska uruchomieniowego).</span><span class="sxs-lookup"><span data-stu-id="a27f0-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="a27f0-129">[ICLRRuntimeHost:: SetHostControl —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="a27f0-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="a27f0-130">[ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="a27f0-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="a27f0-131">Funkcja określona przez parametr `pEndHostSetup`.</span><span class="sxs-lookup"><span data-stu-id="a27f0-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="a27f0-132">Wszystkie wywołania z `pBeginHostSetup` do `pEndHostSetup` muszą wystąpić w pojedynczym wątku lub włókna przy użyciu tego samego logicznego stosu.</span><span class="sxs-lookup"><span data-stu-id="a27f0-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="a27f0-133">Ten wątek może się różnić od wątku, w którym wywołano `hostCallback`.</span><span class="sxs-lookup"><span data-stu-id="a27f0-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a27f0-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a27f0-134">Requirements</span></span>  
 <span data-ttu-id="a27f0-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a27f0-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a27f0-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a27f0-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a27f0-137">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a27f0-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a27f0-138">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a27f0-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a27f0-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a27f0-139">See also</span></span>

- [<span data-ttu-id="a27f0-140">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a27f0-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
