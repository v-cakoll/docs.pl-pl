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
ms.openlocfilehash: 34590744407b25d7d53c06c452fff5bac2a95246
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136384"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="0a4fb-102">ICLRRuntimeInfo::IsStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a4fb-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="0a4fb-103">Wskazuje, czy środowisko uruchomieniowe zostało uruchomione (czyli czy [Metoda ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) została wywołana i została zakończona pomyślnie).</span><span class="sxs-lookup"><span data-stu-id="0a4fb-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a4fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a4fb-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a4fb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a4fb-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="0a4fb-106">[out] `true` w przypadku uruchomienia tego środowiska uruchomieniowego; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="0a4fb-107">określoną Zwraca flagi, które zostały użyte do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a4fb-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0a4fb-108">Return Value</span></span>  
 <span data-ttu-id="0a4fb-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0a4fb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0a4fb-110">HRESULT</span></span>|<span data-ttu-id="0a4fb-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0a4fb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0a4fb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="0a4fb-112">S_OK</span></span>|<span data-ttu-id="0a4fb-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="0a4fb-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="0a4fb-114">E_NOTIMPL</span></span>|<span data-ttu-id="0a4fb-115">Wersja środowiska uruchomieniowego języka wspólnego (CLR) jest wcześniejsza niż wersja środowiska CLR w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a4fb-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a4fb-116">Remarks</span></span>  
 <span data-ttu-id="0a4fb-117">Ta metoda nie działa w przypadku wersji CLR wcześniejszych niż wersja środowiska CLR w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0a4fb-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a4fb-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a4fb-118">Requirements</span></span>  
 <span data-ttu-id="0a4fb-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a4fb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a4fb-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="0a4fb-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0a4fb-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0a4fb-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0a4fb-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a4fb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a4fb-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a4fb-123">See also</span></span>

- [<span data-ttu-id="0a4fb-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a4fb-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0a4fb-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0a4fb-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0a4fb-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="0a4fb-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
