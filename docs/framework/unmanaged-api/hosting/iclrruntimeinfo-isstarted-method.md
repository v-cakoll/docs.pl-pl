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
ms.openlocfilehash: 432de909e1b8166f6d8923889382d9408fb6c62d
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490259"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="d31d5-102">ICLRRuntimeInfo::IsStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="d31d5-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="d31d5-103">Wskazuje, czy środowisko uruchomieniowe zostało rozpoczęte (oznacza to, czy [iclrruntimehost::Start — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) została wywołana i zakończyła się pomyślnie).</span><span class="sxs-lookup"><span data-stu-id="d31d5-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d31d5-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d31d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d31d5-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="d31d5-106">[out] `true` Jeżeli to środowisko wykonawcze jest wprowadzenie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="d31d5-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="d31d5-107">[out] Zwraca wartość flagi, które były używane do uruchamiania w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="d31d5-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d31d5-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d31d5-108">Return Value</span></span>  
 <span data-ttu-id="d31d5-109">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="d31d5-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="d31d5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d31d5-110">HRESULT</span></span>|<span data-ttu-id="d31d5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d31d5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d31d5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d31d5-112">S_OK</span></span>|<span data-ttu-id="d31d5-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d31d5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="d31d5-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="d31d5-114">E_NOTIMPL</span></span>|<span data-ttu-id="d31d5-115">Typowe wersję środowiska uruchomieniowego języka (wspólnego CLR) jest wcześniejsza niż wersja środowiska CLR programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d31d5-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d31d5-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d31d5-116">Remarks</span></span>  
 <span data-ttu-id="d31d5-117">Ta metoda nie działa z wersjami środowiska CLR wcześniejsze niż wersja środowiska CLR programu .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d31d5-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d31d5-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d31d5-118">Requirements</span></span>  
 <span data-ttu-id="d31d5-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d31d5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d31d5-120">**Nagłówek:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="d31d5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d31d5-121">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d31d5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d31d5-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d31d5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31d5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d31d5-123">See also</span></span>

- [<span data-ttu-id="d31d5-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d31d5-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="d31d5-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d31d5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="d31d5-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="d31d5-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
