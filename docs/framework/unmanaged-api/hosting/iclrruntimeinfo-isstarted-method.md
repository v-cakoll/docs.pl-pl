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
ms.openlocfilehash: 85a7adddf395e07297c8fb6ceab4aa81e0aaf012
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762204"
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="9b6fc-102">ICLRRuntimeInfo::IsStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b6fc-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="9b6fc-103">Wskazuje, czy środowisko uruchomieniowe zostało uruchomione (czyli czy [Metoda ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) została wywołana i została zakończona pomyślnie).</span><span class="sxs-lookup"><span data-stu-id="9b6fc-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b6fc-104">Syntax</span></span>  
  
```cpp  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b6fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b6fc-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="9b6fc-106">[out] `true` w przypadku uruchomienia tego środowiska uruchomieniowego; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="9b6fc-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="9b6fc-107">określoną Zwraca flagi, które zostały użyte do uruchomienia środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9b6fc-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b6fc-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b6fc-108">Return Value</span></span>  
 <span data-ttu-id="9b6fc-109">Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="9b6fc-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9b6fc-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b6fc-110">HRESULT</span></span>|<span data-ttu-id="9b6fc-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9b6fc-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9b6fc-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9b6fc-112">S_OK</span></span>|<span data-ttu-id="9b6fc-113">Metoda została ukończona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="9b6fc-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="9b6fc-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="9b6fc-114">E_NOTIMPL</span></span>|<span data-ttu-id="9b6fc-115">Wersja środowiska uruchomieniowego języka wspólnego (CLR) jest wcześniejsza niż wersja środowiska CLR w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b6fc-115">The common language runtime (CLR) version is earlier than the CLR version in the .NET Framework 4.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b6fc-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9b6fc-116">Remarks</span></span>  
 <span data-ttu-id="9b6fc-117">Ta metoda nie działa w przypadku wersji CLR wcześniejszych niż wersja środowiska CLR w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9b6fc-117">This method does not work with CLR versions earlier than the CLR version in the .NET Framework 4.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b6fc-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b6fc-118">Requirements</span></span>  
 <span data-ttu-id="9b6fc-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6fc-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6fc-120">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="9b6fc-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9b6fc-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9b6fc-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b6fc-122">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6fc-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6fc-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b6fc-123">See also</span></span>

- [<span data-ttu-id="9b6fc-124">ICLRRuntimeInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b6fc-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="9b6fc-125">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9b6fc-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9b6fc-126">Hosting</span><span class="sxs-lookup"><span data-stu-id="9b6fc-126">Hosting</span></span>](index.md)
