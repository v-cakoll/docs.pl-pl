---
title: ICLRRuntimeInfo::IsLoadable — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 9339bb974c261e62502c760dfaf45651573cbe1a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136374"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="15f20-102">ICLRRuntimeInfo::IsLoadable — Metoda</span><span class="sxs-lookup"><span data-stu-id="15f20-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="15f20-103">Wskazuje, czy środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane do bieżącego procesu, biorąc pod uwagę inne środowiska uruchomieniowe, które mogły już zostać załadowane do procesu.</span><span class="sxs-lookup"><span data-stu-id="15f20-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15f20-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15f20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15f20-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="15f20-106">[out] `true`, jeśli środowisko uruchomieniowe może zostać załadowane do bieżącego procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="15f20-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15f20-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="15f20-107">Return Value</span></span>  
 <span data-ttu-id="15f20-108">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="15f20-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="15f20-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15f20-109">HRESULT</span></span>|<span data-ttu-id="15f20-110">Opis</span><span class="sxs-lookup"><span data-stu-id="15f20-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15f20-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="15f20-111">S_OK</span></span>|<span data-ttu-id="15f20-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="15f20-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="15f20-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="15f20-113">E_POINTER</span></span>|<span data-ttu-id="15f20-114">`pbLoadable` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="15f20-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15f20-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15f20-115">Remarks</span></span>  
 <span data-ttu-id="15f20-116">Jeśli inne środowisko uruchomieniowe jest już załadowane do procesu, a środowisko uruchomieniowe skojarzone z tym interfejsem może zostać załadowane dla równoczesnego wykonania w procesie, `pbLoadable` zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="15f20-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="15f20-117">Jeśli dwa środowiska uruchomieniowe nie mogą być uruchamiane równolegle w procesie, `pbLoadable` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="15f20-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="15f20-118">Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4 może działać obok siebie w tym samym procesie, przy użyciu środowiska CLR w wersji 2,0 lub CLR w wersji 1,1.</span><span class="sxs-lookup"><span data-stu-id="15f20-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="15f20-119">Jednak środowisko CLR w wersji 1,1 i środowisko CLR w wersji 2,0 nie mogą być uruchamiane równolegle.</span><span class="sxs-lookup"><span data-stu-id="15f20-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="15f20-120">Jeśli żadne środowisko uruchomieniowe nie zostanie załadowane do procesu, ta metoda zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="15f20-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15f20-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15f20-121">Requirements</span></span>  
 <span data-ttu-id="15f20-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15f20-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15f20-123">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="15f20-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="15f20-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="15f20-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15f20-125">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15f20-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f20-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15f20-126">See also</span></span>

- [<span data-ttu-id="15f20-127">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="15f20-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="15f20-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="15f20-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="15f20-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="15f20-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
