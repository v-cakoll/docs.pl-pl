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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6773d9387ae3b91125b413dee51b0c3fcbbb1edd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502023"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="e6e3d-102">ICorRuntimeHost::UnloadDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e6e3d-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="e6e3d-103">Zwalnia domeny określonej aplikacji w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6e3d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e6e3d-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6e3d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e6e3d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e6e3d-106">[in] Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domeny, która ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6e3d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e6e3d-107">Return Value</span></span>  
  
|<span data-ttu-id="e6e3d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e6e3d-108">HRESULT</span></span>|<span data-ttu-id="e6e3d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="e6e3d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e6e3d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6e3d-110">S_OK</span></span>|<span data-ttu-id="e6e3d-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-111">The operation was successful.</span></span>|  
|<span data-ttu-id="e6e3d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e6e3d-112">S_FALSE</span></span>|<span data-ttu-id="e6e3d-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e6e3d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e6e3d-114">E_FAIL</span></span>|<span data-ttu-id="e6e3d-115">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e6e3d-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e6e3d-117">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e6e3d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e6e3d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e6e3d-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e6e3d-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6e3d-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e6e3d-120">Requirements</span></span>  
 <span data-ttu-id="e6e3d-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6e3d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6e3d-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e6e3d-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e6e3d-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e6e3d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e6e3d-124">**Wersja programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e6e3d-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6e3d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6e3d-125">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e6e3d-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e6e3d-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
