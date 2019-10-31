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
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121468"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="57eb2-102">IHostSecurityManager::OpenThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="57eb2-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="57eb2-103">Otwiera token dostępu swobodnego skojarzony z aktualnie wykonywanym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="57eb2-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57eb2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57eb2-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57eb2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57eb2-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="57eb2-106">podczas Maska wartości dostępu określająca żądane typy dostępu do tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="57eb2-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="57eb2-107">Te wartości są zdefiniowane w funkcji `OpenThreadToken` Win32.</span><span class="sxs-lookup"><span data-stu-id="57eb2-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="57eb2-108">Żądane typy dostępu są uzgadniane z poufną listą kontroli dostępu (DACL) tokenu, aby określić, które typy dostępu mają być udzielone lub odrzucane.</span><span class="sxs-lookup"><span data-stu-id="57eb2-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="57eb2-109">[in] `true`, aby określić, że sprawdzanie dostępu należy przeprowadzić przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego; `false`, aby określić, że sprawdzanie dostępu ma być wykonywane przy użyciu kontekstu zabezpieczeń dla samego wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="57eb2-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="57eb2-110">Jeśli wątek personifikuje klienta, kontekst zabezpieczeń może być procesem klienta.</span><span class="sxs-lookup"><span data-stu-id="57eb2-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="57eb2-111">określoną Wskaźnik do nowo otwartego tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="57eb2-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57eb2-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="57eb2-112">Return Value</span></span>  
  
|<span data-ttu-id="57eb2-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57eb2-113">HRESULT</span></span>|<span data-ttu-id="57eb2-114">Opis</span><span class="sxs-lookup"><span data-stu-id="57eb2-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57eb2-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="57eb2-115">S_OK</span></span>|<span data-ttu-id="57eb2-116">`OpenThreadToken` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="57eb2-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="57eb2-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57eb2-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57eb2-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="57eb2-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="57eb2-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="57eb2-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="57eb2-120">Upłynął limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="57eb2-120">The call timed out.</span></span>|  
|<span data-ttu-id="57eb2-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="57eb2-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="57eb2-122">Obiekt wywołujący nie jest właocicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="57eb2-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="57eb2-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="57eb2-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="57eb2-124">Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.</span><span class="sxs-lookup"><span data-stu-id="57eb2-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="57eb2-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57eb2-125">E_FAIL</span></span>|<span data-ttu-id="57eb2-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="57eb2-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="57eb2-127">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="57eb2-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="57eb2-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57eb2-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57eb2-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57eb2-129">Remarks</span></span>  
 <span data-ttu-id="57eb2-130">`IHostSecurityManager::OpenThreadToken` zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 zezwala obiektowi wywołującemu na przekazywanie dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="57eb2-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="57eb2-131">Typ `HANDLE` nie jest zgodny z modelem COM, oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga kierowania niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="57eb2-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="57eb2-132">W ten sposób token jest używany tylko w ramach procesu, między środowiskiem CLR a hostem.</span><span class="sxs-lookup"><span data-stu-id="57eb2-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57eb2-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57eb2-133">Requirements</span></span>  
 <span data-ttu-id="57eb2-134">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57eb2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57eb2-135">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="57eb2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57eb2-136">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="57eb2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57eb2-137">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57eb2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57eb2-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57eb2-138">See also</span></span>

- [<span data-ttu-id="57eb2-139">IHostSecurityContext, interfejs</span><span class="sxs-lookup"><span data-stu-id="57eb2-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="57eb2-140">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="57eb2-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
