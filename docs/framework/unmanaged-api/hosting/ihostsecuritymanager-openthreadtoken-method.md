---
title: IHostSecurityManager::OpenThreadToken — Metoda
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68ebfdcd0ef34edec724a044791d05dd48580b12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144563"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="d800b-102">IHostSecurityManager::OpenThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="d800b-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="d800b-103">Zostanie otwarty token dostępu skojarzone z aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="d800b-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d800b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d800b-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d800b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d800b-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="d800b-106">[in] Maska wartości dostępu, które określają żądany typ dostępu do tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="d800b-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="d800b-107">Te wartości są zdefiniowane w Win32 `OpenThreadToken` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d800b-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="d800b-108">Typy żądanego dostępu są uzgodnione względem listy kontroli dostępu tokenu (DACL), aby określić, jakie typy dostępu, aby udzielić lub odmówić.</span><span class="sxs-lookup"><span data-stu-id="d800b-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="d800b-109">[in] `true` do określenia, że należy dokonać kontroli dostępu za pomocą kontekstu zabezpieczeń procesu wywołującego wątku; `false` do określenia, czy należy wykonać sprawdzanie dostępu za pomocą kontekstu zabezpieczeń dla wątku wywołującego, sam.</span><span class="sxs-lookup"><span data-stu-id="d800b-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="d800b-110">Jeśli wątek nie personifikuje klienta, kontekstu zabezpieczeń może być procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="d800b-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="d800b-111">[out] Wskaźnik do tokena dostępu w nowo otwartym.</span><span class="sxs-lookup"><span data-stu-id="d800b-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d800b-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d800b-112">Return Value</span></span>  
  
|<span data-ttu-id="d800b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d800b-113">HRESULT</span></span>|<span data-ttu-id="d800b-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d800b-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d800b-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="d800b-115">S_OK</span></span>|`OpenThreadToken` <span data-ttu-id="d800b-116">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="d800b-116">returned successfully.</span></span>|  
|<span data-ttu-id="d800b-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d800b-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d800b-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d800b-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d800b-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d800b-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d800b-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="d800b-120">The call timed out.</span></span>|  
|<span data-ttu-id="d800b-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d800b-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d800b-122">Obiekt wywołujący nie posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="d800b-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d800b-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d800b-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d800b-124">Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="d800b-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d800b-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d800b-125">E_FAIL</span></span>|<span data-ttu-id="d800b-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="d800b-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d800b-127">Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="d800b-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d800b-128">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d800b-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d800b-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d800b-129">Remarks</span></span>  
 `IHostSecurityManager::OpenThreadToken` <span data-ttu-id="d800b-130">zachowuje się podobnie do odpowiednich funkcji Win32 o takiej samej nazwie, z tą różnicą, że funkcja Win32 pozwala na obiekt wywołujący, aby przekazać dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::OpenThreadToken` otwiera token skojarzony wątek wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d800b-130">behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="d800b-131">`HANDLE` Typ nie jest zgodny z COM, oznacza to, że jego rozmiar jest specyficzne dla systemu operacyjnego i wymaga ona organizowanie niestandardowe.</span><span class="sxs-lookup"><span data-stu-id="d800b-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="d800b-132">W związku z tym ten token jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="d800b-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d800b-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d800b-133">Requirements</span></span>  
 <span data-ttu-id="d800b-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d800b-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d800b-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d800b-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d800b-136">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d800b-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="d800b-137">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d800b-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d800b-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d800b-138">See also</span></span>

- [<span data-ttu-id="d800b-139">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d800b-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="d800b-140">IHostSecurityManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d800b-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
