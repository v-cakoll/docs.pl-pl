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
ms.openlocfilehash: 3275a69683a312340f35841815685066def10b23
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762529"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="860b0-102">ICLRRuntimeInfo::IsLoaded — Metoda</span><span class="sxs-lookup"><span data-stu-id="860b0-102">ICLRRuntimeInfo::IsLoaded Method</span></span>
<span data-ttu-id="860b0-103">Wskazuje, czy środowisko uruchomieniowe języka wspólnego (CLR) skojarzone z interfejsem [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) jest załadowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="860b0-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="860b0-104">Środowisko uruchomieniowe może zostać załadowane bez również uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="860b0-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860b0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="860b0-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="860b0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="860b0-106">Parameters</span></span>  
 `hndProcess`  
 <span data-ttu-id="860b0-107">podczas Dojście do procesu.</span><span class="sxs-lookup"><span data-stu-id="860b0-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="860b0-108">[out] `true` Jeśli środowisko CLR jest załadowane do procesu; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="860b0-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="860b0-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="860b0-109">Return Value</span></span>  
 <span data-ttu-id="860b0-110">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="860b0-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="860b0-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="860b0-111">HRESULT</span></span>|<span data-ttu-id="860b0-112">Opis</span><span class="sxs-lookup"><span data-stu-id="860b0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="860b0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="860b0-113">S_OK</span></span>|<span data-ttu-id="860b0-114">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="860b0-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="860b0-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="860b0-115">E_POINTER</span></span>|<span data-ttu-id="860b0-116">`pbLoaded`ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="860b0-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="860b0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="860b0-117">Remarks</span></span>  
 <span data-ttu-id="860b0-118">Ta metoda jest zgodna z poprzednimi wersjami przy użyciu następujących funkcji i interfejsów:</span><span class="sxs-lookup"><span data-stu-id="860b0-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="860b0-119">Interfejs [ICorRuntimeHost](icorruntimehost-interface.md) (w interfejsie API hostingu .NET Framework w wersji 1).</span><span class="sxs-lookup"><span data-stu-id="860b0-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="860b0-120">Interfejs [ICLRRuntimeHost](iclrruntimehost-interface.md) (w interfejsie API hostingu .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="860b0-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="860b0-121">Przestarzałe `CorBindTo*` funkcje (zobacz [przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md) w interfejsie API hostingu .NET Framework 2,0).</span><span class="sxs-lookup"><span data-stu-id="860b0-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="860b0-122">Host może wywołać jedną z przestarzałych `CorBindTo*` funkcji, takich jak funkcja [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) , aby utworzyć wystąpienie konkretnej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="860b0-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="860b0-123">Następnie host może wywołać metodę [ICLRMetaHost:: GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) i określić ten sam numer wersji, aby uzyskać Interfejs [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="860b0-123">The host could then call the [ICLRMetaHost::GetRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="860b0-124">Jeśli host następnie wywoła `IsLoaded` metodę w zwróconym interfejsie [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , `pbLoaded` zwraca `true` ; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="860b0-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="860b0-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="860b0-125">Requirements</span></span>  
 <span data-ttu-id="860b0-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="860b0-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="860b0-127">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="860b0-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="860b0-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="860b0-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="860b0-129">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="860b0-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860b0-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="860b0-130">See also</span></span>

- [<span data-ttu-id="860b0-131">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="860b0-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="860b0-132">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="860b0-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="860b0-133">Hosting</span><span class="sxs-lookup"><span data-stu-id="860b0-133">Hosting</span></span>](index.md)
