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
ms.openlocfilehash: 11d042ea9eecc8d428761da6eaa15f7c2907ebd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176269"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="0f03e-102">IHostSecurityManager::OpenThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f03e-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="0f03e-103">Otwiera token dostępu uznaniowego skojarzony z aktualnie wykonywanym wątkiem.</span><span class="sxs-lookup"><span data-stu-id="0f03e-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f03e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f03e-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,
    [in]  BOOL     bOpenAsSelf,
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f03e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f03e-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="0f03e-106">[w] Maska wartości dostępu, które określają żądane typy dostępu do tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="0f03e-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="0f03e-107">Wartości te są zdefiniowane `OpenThreadToken` w funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="0f03e-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="0f03e-108">Żądane typy dostępu są uzgadniane z listy kontroli dostępu (DACL) tokenu, aby określić, które typy dostępu do udzielenia lub odmowy.</span><span class="sxs-lookup"><span data-stu-id="0f03e-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="0f03e-109">[w] `true` określenie, że kontrola dostępu powinna być przeprowadzana przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego; `false` , aby określić, że sprawdzanie dostępu powinny być wykonywane przy użyciu kontekstu zabezpieczeń dla samego wątku wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0f03e-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="0f03e-110">Jeśli wątek personifikuje klienta, kontekst zabezpieczeń może być kontekstu procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="0f03e-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="0f03e-111">[na zewnątrz] Wskaźnik do nowo otwartego tokenu dostępu.</span><span class="sxs-lookup"><span data-stu-id="0f03e-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f03e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f03e-112">Return Value</span></span>  
  
|<span data-ttu-id="0f03e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f03e-113">HRESULT</span></span>|<span data-ttu-id="0f03e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="0f03e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f03e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f03e-115">S_OK</span></span>|<span data-ttu-id="0f03e-116">`OpenThreadToken`zwrócono pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0f03e-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="0f03e-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f03e-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f03e-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchomić kod zarządzany lub proces wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="0f03e-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f03e-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f03e-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f03e-120">Limit czasu połączenia.</span><span class="sxs-lookup"><span data-stu-id="0f03e-120">The call timed out.</span></span>|  
|<span data-ttu-id="0f03e-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f03e-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f03e-122">Wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="0f03e-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f03e-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f03e-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f03e-124">Zdarzenie zostało anulowane, gdy czekał na niego zablokowany wątek lub włókno.</span><span class="sxs-lookup"><span data-stu-id="0f03e-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f03e-125">E_fail</span><span class="sxs-lookup"><span data-stu-id="0f03e-125">E_FAIL</span></span>|<span data-ttu-id="0f03e-126">Doszło do nieznanej katastrofalnej awarii.</span><span class="sxs-lookup"><span data-stu-id="0f03e-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f03e-127">Gdy metoda zwraca E_FAIL, CLR nie jest już użyteczny w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="0f03e-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f03e-128">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0f03e-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f03e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f03e-129">Remarks</span></span>  
 <span data-ttu-id="0f03e-130">`IHostSecurityManager::OpenThreadToken`zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 umożliwia obiektowi wywołującemu przekazywanie w dojściu do dowolnego wątku, podczas gdy `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="0f03e-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="0f03e-131">Typ `HANDLE` nie jest zgodny z com, oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga niestandardowego organizowania.</span><span class="sxs-lookup"><span data-stu-id="0f03e-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="0f03e-132">W związku z tym ten token jest do użytku tylko w ramach procesu, między CLR i hosta.</span><span class="sxs-lookup"><span data-stu-id="0f03e-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f03e-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f03e-133">Requirements</span></span>  
 <span data-ttu-id="0f03e-134">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f03e-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f03e-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f03e-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f03e-136">**Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0f03e-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f03e-137">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f03e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f03e-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f03e-138">See also</span></span>

- [<span data-ttu-id="0f03e-139">IHostSecurityContext — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0f03e-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [<span data-ttu-id="0f03e-140">IHostSecurityManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f03e-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
