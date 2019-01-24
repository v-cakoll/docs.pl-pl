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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9780020abe609212fe3c4bd65f70200467ff9c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533692"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="cdf52-102">ICLRRuntimeInfo::IsLoadable — Metoda</span><span class="sxs-lookup"><span data-stu-id="cdf52-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="cdf52-103">Wskazuje, czy środowisko uruchomieniowe skojarzona z tym interfejsem, może być załadowany do bieżącego procesu, biorąc pod uwagę innych środowisk wykonawczych, które mogą już być załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="cdf52-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdf52-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdf52-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdf52-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="cdf52-106">[out] `true` Jeżeli to środowisko wykonawcze może być załadowany do bieżącego procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="cdf52-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdf52-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cdf52-107">Return Value</span></span>  
 <span data-ttu-id="cdf52-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="cdf52-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="cdf52-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdf52-109">HRESULT</span></span>|<span data-ttu-id="cdf52-110">Opis</span><span class="sxs-lookup"><span data-stu-id="cdf52-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdf52-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cdf52-111">S_OK</span></span>|<span data-ttu-id="cdf52-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cdf52-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="cdf52-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="cdf52-113">E_POINTER</span></span>|<span data-ttu-id="cdf52-114">`pbLoadable` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="cdf52-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf52-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdf52-115">Remarks</span></span>  
 <span data-ttu-id="cdf52-116">Jeśli innego środowiska uruchomieniowego jest już załadowany do procesu i środowiska uruchomieniowego skojarzona z tym interfejsem, mogą być ładowane w trakcie wykonywania side-by-side, `pbLoadable` zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="cdf52-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="cdf52-117">Jeśli dwa środowiska uruchomieniowe, nie można uruchomić side-by-side w procesie, `pbLoadable` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="cdf52-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="cdf52-118">Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4, można uruchomić side-by-side jest ten sam proces, za pomocą środowiska CLR w wersji 2.0 lub środowisko CLR w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="cdf52-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="cdf52-119">Środowisko CLR w wersji 1.1 i środowisko CLR w wersji 2.0 nie można jednak uruchomić side-by-side w procesie.</span><span class="sxs-lookup"><span data-stu-id="cdf52-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="cdf52-120">Jeśli bez środowisk uruchomieniowych są ładowane do procesu, ta metoda zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="cdf52-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf52-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdf52-121">Requirements</span></span>  
 <span data-ttu-id="cdf52-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdf52-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdf52-123">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="cdf52-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cdf52-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cdf52-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdf52-125">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdf52-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf52-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdf52-126">See also</span></span>
- [<span data-ttu-id="cdf52-127">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="cdf52-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="cdf52-128">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cdf52-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="cdf52-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="cdf52-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
