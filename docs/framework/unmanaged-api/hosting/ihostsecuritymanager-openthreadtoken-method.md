---
title: "IHostSecurityManager::OpenThreadToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSecurityManager.OpenThreadToken
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5d3b5ec31944b58bec6268de6e54503141880e6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a><span data-ttu-id="7c390-102">IHostSecurityManager::OpenThreadToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c390-102">IHostSecurityManager::OpenThreadToken Method</span></span>
<span data-ttu-id="7c390-103">Otwiera token dostępu skojarzony z wątkiem aktualnie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="7c390-103">Opens the discretionary access token associated with the currently executing thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c390-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c390-104">Syntax</span></span>  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c390-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c390-105">Parameters</span></span>  
 `dwDesiredAccess`  
 <span data-ttu-id="7c390-106">[in] Maska wartości dostępu, które określają żądanych typów dostęp do tokenu wątku.</span><span class="sxs-lookup"><span data-stu-id="7c390-106">[in] A mask of access values that specify the requested types of access to the thread token.</span></span> <span data-ttu-id="7c390-107">Te wartości są definiowane w Win32 `OpenThreadToken` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7c390-107">These values are defined in the Win32 `OpenThreadToken` function.</span></span> <span data-ttu-id="7c390-108">Typy żądany dostęp są uzgadniane przed tokenu poufnej listy kontroli dostępu (DACL), aby określić, jakie typy dostępu do Udziel lub Odmów.</span><span class="sxs-lookup"><span data-stu-id="7c390-108">The requested access types are reconciled against the token's discretionary access control list (DACL) to determine which types of access to grant or deny.</span></span>  
  
 `bOpenAsSelf`  
 <span data-ttu-id="7c390-109">[in] `true` do określenia, czy należy dokonać kontroli dostępu w kontekście zabezpieczeń procesu, wątku wywołującym; `false` do określenia, czy należy wykonać sprawdzanie dostępu przy użyciu kontekstu zabezpieczeń dla sam wątek wywołujący.</span><span class="sxs-lookup"><span data-stu-id="7c390-109">[in] `true` to specify that the access check should be made using the security context of the process for the calling thread; `false` to specify that the access check should be performed using the security context for the calling thread itself.</span></span> <span data-ttu-id="7c390-110">Jeśli wątek personifikuje klienta, kontekstu zabezpieczeń może być procesu klienta.</span><span class="sxs-lookup"><span data-stu-id="7c390-110">If the thread is impersonating a client, the security context can be that of a client process.</span></span>  
  
 `phThreadToken`  
 <span data-ttu-id="7c390-111">[out] Wskaźnik do tokena dostępu w nowo otwartym.</span><span class="sxs-lookup"><span data-stu-id="7c390-111">[out] A pointer to the newly opened access token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c390-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7c390-112">Return Value</span></span>  
  
|<span data-ttu-id="7c390-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c390-113">HRESULT</span></span>|<span data-ttu-id="7c390-114">Opis</span><span class="sxs-lookup"><span data-stu-id="7c390-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c390-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c390-115">S_OK</span></span>|<span data-ttu-id="7c390-116">`OpenThreadToken`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7c390-116">`OpenThreadToken` returned successfully.</span></span>|  
|<span data-ttu-id="7c390-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c390-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c390-118">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7c390-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c390-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c390-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c390-120">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7c390-120">The call timed out.</span></span>|  
|<span data-ttu-id="7c390-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c390-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c390-122">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7c390-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c390-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c390-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c390-124">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7c390-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c390-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c390-125">E_FAIL</span></span>|<span data-ttu-id="7c390-126">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7c390-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c390-127">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7c390-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c390-128">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c390-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c390-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c390-129">Remarks</span></span>  
 <span data-ttu-id="7c390-130">`IHostSecurityManager::OpenThreadToken`działa podobnie do funkcji Win32 odpowiedniego o takiej samej nazwie, z tą różnicą, że funkcja Win32 umożliwia obiekt wywołujący, aby przekazać w dojścia do dowolnego wątku, podczas `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.</span><span class="sxs-lookup"><span data-stu-id="7c390-130">`IHostSecurityManager::OpenThreadToken` behaves similarly to the corresponding Win32 function of the same name, except that the Win32 function allows the caller to pass in a handle to an arbitrary thread, while `IHostSecurityManager::OpenThreadToken` opens only the token associated with the calling thread.</span></span>  
  
 <span data-ttu-id="7c390-131">`HANDLE` Typ nie jest zgodny z interfejsem COM, oznacza to, jego rozmiar jest specyficzna dla systemu operacyjnego i wymaga przekazywanie niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7c390-131">The `HANDLE` type is not COM-compliant, that is, its size is specific to the operating system, and it requires custom marshaling.</span></span> <span data-ttu-id="7c390-132">W związku z tym token ten jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.</span><span class="sxs-lookup"><span data-stu-id="7c390-132">Thus, this token is for use only within the process, between the CLR and the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c390-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c390-133">Requirements</span></span>  
 <span data-ttu-id="7c390-134">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c390-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c390-135">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c390-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c390-136">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c390-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c390-137">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c390-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c390-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c390-138">See Also</span></span>  
 [<span data-ttu-id="7c390-139">IHostSecurityContext — interfejs</span><span class="sxs-lookup"><span data-stu-id="7c390-139">IHostSecurityContext Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [<span data-ttu-id="7c390-140">IHostSecurityManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7c390-140">IHostSecurityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
