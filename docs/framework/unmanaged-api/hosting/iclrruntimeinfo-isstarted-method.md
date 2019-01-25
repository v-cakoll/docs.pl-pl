---
title: ICLRRuntimeInfo::IsStarted — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb23a8e4237ff9b4b217458150c1f04956e439ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526599"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="45864-102">ICLRRuntimeInfo::IsStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="45864-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="45864-103">Wskazuje, czy środowisko uruchomieniowe zostało rozpoczęte (oznacza to, czy [iclrruntimehost::Start — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) została wywołana i zakończyła się pomyślnie).</span><span class="sxs-lookup"><span data-stu-id="45864-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45864-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45864-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45864-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45864-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="45864-106">[out] `true` Jeżeli to środowisko wykonawcze jest wprowadzenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="45864-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="45864-107">[out] Zwraca wartość flagi, które były używane do uruchamiania w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="45864-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45864-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="45864-108">Return Value</span></span>  
 <span data-ttu-id="45864-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="45864-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="45864-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45864-110">HRESULT</span></span>|<span data-ttu-id="45864-111">Opis</span><span class="sxs-lookup"><span data-stu-id="45864-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45864-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="45864-112">S_OK</span></span>|<span data-ttu-id="45864-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="45864-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="45864-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="45864-114">E_NOTIMPL</span></span>|<span data-ttu-id="45864-115">Typowe wersję środowiska uruchomieniowego języka (wspólnego CLR) jest starsza niż wersja środowiska CLR [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45864-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45864-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45864-116">Remarks</span></span>  
 <span data-ttu-id="45864-117">Ta metoda nie działa z wersji środowiska CLR wcześniejsze niż wersja środowiska CLR [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="45864-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45864-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45864-118">Requirements</span></span>  
 <span data-ttu-id="45864-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45864-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45864-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="45864-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="45864-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45864-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45864-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45864-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45864-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45864-123">See also</span></span>
- [<span data-ttu-id="45864-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="45864-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="45864-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45864-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="45864-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="45864-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
