---
title: ICLRRuntimeInfo::IsLoaded — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 45e27ac3c2d4912d2ed3e5d43ea3020b9db5dbdc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504033"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="e02f3-102">ICLRRuntimeInfo::IsLoaded — Metoda</span><span class="sxs-lookup"><span data-stu-id="e02f3-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="e02f3-103">Wskazuje, czy środowisko uruchomieniowe języka wspólnego (CLR) skojarzone z interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) jest załadowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="e02f3-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="e02f3-104">Środowisko uruchomieniowe może zostać załadowane bez również uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e02f3-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e02f3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e02f3-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e02f3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e02f3-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="e02f3-107">podczas Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="e02f3-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="e02f3-108">[out] `true` Jeśli środowisko CLR jest załadowane do procesu; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="e02f3-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e02f3-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e02f3-109">Return Value</span></span>  
 <span data-ttu-id="e02f3-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="e02f3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e02f3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e02f3-111">HRESULT</span></span>|<span data-ttu-id="e02f3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e02f3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e02f3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e02f3-113">S_OK</span></span>|<span data-ttu-id="e02f3-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e02f3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="e02f3-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="e02f3-115">E_POINTER</span></span>|<span data-ttu-id="e02f3-116">`pbLoaded`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="e02f3-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e02f3-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e02f3-117">Remarks</span></span>  
 <span data-ttu-id="e02f3-118">Ta metoda jest zgodna z poprzednimi wersjami przy użyciu następujących funkcji i interfejsów:</span><span class="sxs-lookup"><span data-stu-id="e02f3-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="e02f3-119">Interfejs [ICorRuntimeHost](icorruntimehost-interface.md) (w interfejsie API hostingu .NET Framework w wersji 1).</span><span class="sxs-lookup"><span data-stu-id="e02f3-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="e02f3-120">Interfejs [ICLRRuntimeHost](iclrruntimehost-interface.md) (w interfejsie API hostingu .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="e02f3-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="e02f3-121">Przestarzałe `CorBindTo*` funkcje (zobacz [przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md) w interfejsie API hostingu .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="e02f3-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="e02f3-122">Host może wywołać jedną z przestarzałych `CorBindTo*` funkcji, takich jak funkcja [CorBindToRuntime](corbindtoruntime-function.md) , aby utworzyć wystąpienie konkretnej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="e02f3-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="e02f3-123">Następnie host może wywołać metodę [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) i określić ten sam numer wersji, aby uzyskać Interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="e02f3-123">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="e02f3-124">Jeśli host następnie wywoła `IsLoaded` metodę w zwróconym interfejsie [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` zwraca `true` ; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="e02f3-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e02f3-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e02f3-125">Requirements</span></span>  
 <span data-ttu-id="e02f3-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e02f3-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e02f3-127">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="e02f3-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e02f3-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e02f3-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e02f3-129">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e02f3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e02f3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e02f3-130">See also</span></span>

- [<span data-ttu-id="e02f3-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e02f3-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e02f3-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e02f3-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="e02f3-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="e02f3-133">Hosting</span></span>](index.md)
