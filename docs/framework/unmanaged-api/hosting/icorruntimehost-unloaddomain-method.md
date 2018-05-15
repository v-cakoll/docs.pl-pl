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
ms.openlocfilehash: c4db96133315b23a2d0b4bd32b597ee03f5d697b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="df18b-102">ICorRuntimeHost::UnloadDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="df18b-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="df18b-103">Zwalnia domeny określonej aplikacji w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="df18b-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df18b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df18b-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df18b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df18b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="df18b-106">[in] Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domeny, która ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="df18b-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df18b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="df18b-107">Return Value</span></span>  
  
|<span data-ttu-id="df18b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df18b-108">HRESULT</span></span>|<span data-ttu-id="df18b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="df18b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df18b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="df18b-110">S_OK</span></span>|<span data-ttu-id="df18b-111">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="df18b-111">The operation was successful.</span></span>|  
|<span data-ttu-id="df18b-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="df18b-112">S_FALSE</span></span>|<span data-ttu-id="df18b-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="df18b-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="df18b-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="df18b-114">E_FAIL</span></span>|<span data-ttu-id="df18b-115">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="df18b-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="df18b-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="df18b-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="df18b-117">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="df18b-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="df18b-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="df18b-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="df18b-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="df18b-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df18b-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df18b-120">Requirements</span></span>  
 <span data-ttu-id="df18b-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df18b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df18b-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="df18b-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="df18b-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df18b-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df18b-124">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="df18b-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df18b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df18b-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="df18b-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="df18b-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
