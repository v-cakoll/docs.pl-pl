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
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101591"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="8e5dc-102">ICLRRuntimeInfo::IsLoadable — Metoda</span><span class="sxs-lookup"><span data-stu-id="8e5dc-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="8e5dc-103">Wskazuje, czy środowisko uruchomieniowe skojarzona z tym interfejsem, może być załadowany do bieżącego procesu, biorąc pod uwagę innych środowisk wykonawczych, które mogą już być załadowany do procesu.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e5dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e5dc-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e5dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8e5dc-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="8e5dc-106">[out] `true` Jeżeli to środowisko wykonawcze może być załadowany do bieżącego procesu; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e5dc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8e5dc-107">Return Value</span></span>  
 <span data-ttu-id="8e5dc-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8e5dc-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8e5dc-109">HRESULT</span></span>|<span data-ttu-id="8e5dc-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8e5dc-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e5dc-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8e5dc-111">S_OK</span></span>|<span data-ttu-id="8e5dc-112">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="8e5dc-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8e5dc-113">E_POINTER</span></span>|`pbLoadable` <span data-ttu-id="8e5dc-114">ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-114">is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e5dc-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e5dc-115">Remarks</span></span>  
 <span data-ttu-id="8e5dc-116">Jeśli innego środowiska uruchomieniowego jest już załadowany do procesu i środowiska uruchomieniowego skojarzona z tym interfejsem, mogą być ładowane w trakcie wykonywania side-by-side, `pbLoadable` zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="8e5dc-117">Jeśli dwa środowiska uruchomieniowe, nie można uruchomić side-by-side w procesie, `pbLoadable` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="8e5dc-118">Na przykład środowisko uruchomieniowe języka wspólnego (CLR) w wersji 4, można uruchomić side-by-side jest ten sam proces, za pomocą środowiska CLR w wersji 2.0 lub środowisko CLR w wersji 1.1.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="8e5dc-119">Środowisko CLR w wersji 1.1 i środowisko CLR w wersji 2.0 nie można jednak uruchomić side-by-side w procesie.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="8e5dc-120">Jeśli bez środowisk uruchomieniowych są ładowane do procesu, ta metoda zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="8e5dc-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e5dc-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e5dc-121">Requirements</span></span>  
 <span data-ttu-id="8e5dc-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e5dc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e5dc-123">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8e5dc-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8e5dc-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8e5dc-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="8e5dc-125">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8e5dc-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e5dc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8e5dc-126">See also</span></span>

- [<span data-ttu-id="8e5dc-127">ICLRRuntimeInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8e5dc-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="8e5dc-128">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="8e5dc-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="8e5dc-129">Hosting</span><span class="sxs-lookup"><span data-stu-id="8e5dc-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
