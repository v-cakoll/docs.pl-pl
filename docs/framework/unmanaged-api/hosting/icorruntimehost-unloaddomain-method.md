---
title: ICorRuntimeHost::UnloadDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: dfdcb9b8aedeb3ccbbd27864e79ce43338942922
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133357"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="4bdce-102">ICorRuntimeHost::UnloadDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="4bdce-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="4bdce-103">Zwalnia określoną domenę aplikacji z bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="4bdce-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bdce-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bdce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bdce-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="4bdce-106">podczas Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domenę, która ma zostać zwolniona.</span><span class="sxs-lookup"><span data-stu-id="4bdce-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdce-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bdce-107">Return Value</span></span>  
  
|<span data-ttu-id="4bdce-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdce-108">HRESULT</span></span>|<span data-ttu-id="4bdce-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4bdce-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdce-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdce-110">S_OK</span></span>|<span data-ttu-id="4bdce-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4bdce-111">The operation was successful.</span></span>|  
|<span data-ttu-id="4bdce-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4bdce-112">S_FALSE</span></span>|<span data-ttu-id="4bdce-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="4bdce-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="4bdce-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdce-114">E_FAIL</span></span>|<span data-ttu-id="4bdce-115">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="4bdce-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4bdce-116">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="4bdce-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4bdce-117">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4bdce-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bdce-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdce-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdce-119">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4bdce-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4bdce-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bdce-120">Requirements</span></span>  
 <span data-ttu-id="4bdce-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdce-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdce-122">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4bdce-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdce-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4bdce-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdce-124">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="4bdce-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdce-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bdce-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="4bdce-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="4bdce-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
