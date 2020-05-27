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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008498"
---
# <a name="lockclrversion-function"></a><span data-ttu-id="a5eed-102">LockClrVersion — Funkcja</span><span class="sxs-lookup"><span data-stu-id="a5eed-102">LockClrVersion Function</span></span>
<span data-ttu-id="a5eed-103">Umożliwia hostowi określenie, która wersja środowiska uruchomieniowego języka wspólnego (CLR) zostanie użyta w procesie przed jawnym inicjalizacją środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a5eed-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="a5eed-104">Ta funkcja jest przestarzała w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a5eed-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5eed-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5eed-105">Syntax</span></span>  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5eed-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5eed-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="a5eed-107">podczas Funkcja, która ma zostać wywołana przez środowisko CLR po inicjacji.</span><span class="sxs-lookup"><span data-stu-id="a5eed-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="a5eed-108">podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania o uruchamianiu CLR.</span><span class="sxs-lookup"><span data-stu-id="a5eed-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="a5eed-109">podczas Funkcja, która ma zostać wywołana przez hosta w celu poinformowania środowiska CLR o ukończeniu inicjalizacji.</span><span class="sxs-lookup"><span data-stu-id="a5eed-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a5eed-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a5eed-110">Return Value</span></span>  
 <span data-ttu-id="a5eed-111">Ta metoda zwraca standardowe kody błędów COM, jak zdefiniowano w WinError. h, oprócz następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="a5eed-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a5eed-112">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="a5eed-112">Return code</span></span>|<span data-ttu-id="a5eed-113">Opis</span><span class="sxs-lookup"><span data-stu-id="a5eed-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a5eed-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a5eed-114">S_OK</span></span>|<span data-ttu-id="a5eed-115">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="a5eed-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="a5eed-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a5eed-116">E_INVALIDARG</span></span>|<span data-ttu-id="a5eed-117">Co najmniej jeden argument ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="a5eed-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5eed-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5eed-118">Remarks</span></span>  
 <span data-ttu-id="a5eed-119">Host wywołuje `LockClrVersion` przed zainicjowaniem środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="a5eed-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="a5eed-120">`LockClrVersion`Pobiera trzy parametry, z których wszystkie są wywołaniami zwrotnymi typu [FLockClrVersionCallback —](flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="a5eed-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="a5eed-121">Ten typ jest definiowany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a5eed-121">This type is defined as follows.</span></span>  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="a5eed-122">Następujące kroki są wykonywane po zainicjowaniu środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="a5eed-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1. <span data-ttu-id="a5eed-123">Host wywołuje [CorBindToRuntimeEx](corbindtoruntimeex-function.md) lub jedną z innych funkcji inicjalizacji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a5eed-123">The host calls [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="a5eed-124">Alternatywnie host może zainicjować środowisko uruchomieniowe przy użyciu funkcji aktywacji obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="a5eed-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2. <span data-ttu-id="a5eed-125">Środowisko uruchomieniowe wywołuje funkcję określoną przez `hostCallback` parametr.</span><span class="sxs-lookup"><span data-stu-id="a5eed-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3. <span data-ttu-id="a5eed-126">Funkcja określona przez `hostCallback` then wykonuje następującą sekwencję wywołań:</span><span class="sxs-lookup"><span data-stu-id="a5eed-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    - <span data-ttu-id="a5eed-127">Funkcja określona przez `pBeginHostSetup` parametr.</span><span class="sxs-lookup"><span data-stu-id="a5eed-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    - <span data-ttu-id="a5eed-128">`CorBindToRuntimeEx`(lub inna funkcja inicjacji środowiska uruchomieniowego).</span><span class="sxs-lookup"><span data-stu-id="a5eed-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    - <span data-ttu-id="a5eed-129">[ICLRRuntimeHost:: SetHostControl —](iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5eed-129">[ICLRRuntimeHost::SetHostControl](iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    - <span data-ttu-id="a5eed-130">[ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="a5eed-130">[ICLRRuntimeHost::Start](iclrruntimehost-start-method.md).</span></span>  
  
    - <span data-ttu-id="a5eed-131">Funkcja określona przez `pEndHostSetup` parametr.</span><span class="sxs-lookup"><span data-stu-id="a5eed-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="a5eed-132">Wszystkie wywołania z `pBeginHostSetup` programu `pEndHostSetup` muszą odbywać się w pojedynczym wątku lub włókna przy użyciu tego samego stosu logicznego.</span><span class="sxs-lookup"><span data-stu-id="a5eed-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="a5eed-133">Ten wątek może się różnić od wątku, w którym `hostCallback` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="a5eed-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5eed-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5eed-134">Requirements</span></span>  
 <span data-ttu-id="a5eed-135">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5eed-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5eed-136">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a5eed-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a5eed-137">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a5eed-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5eed-138">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5eed-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5eed-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5eed-139">See also</span></span>

- [<span data-ttu-id="a5eed-140">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="a5eed-140">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
