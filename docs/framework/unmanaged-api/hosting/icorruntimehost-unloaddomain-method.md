---
title: "ICorRuntimeHost::UnloadDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.UnloadDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 054615e08da785f34be59c52488b8a4dcc2d7d98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="57bb3-102">ICorRuntimeHost::UnloadDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="57bb3-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="57bb3-103">Zwalnia domeny określonej aplikacji w bieżącym procesie.</span><span class="sxs-lookup"><span data-stu-id="57bb3-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57bb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57bb3-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="57bb3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57bb3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="57bb3-106">[in] Wskaźnik typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domeny, która ma zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="57bb3-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57bb3-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="57bb3-107">Return Value</span></span>  
  
|<span data-ttu-id="57bb3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="57bb3-108">HRESULT</span></span>|<span data-ttu-id="57bb3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="57bb3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57bb3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="57bb3-110">S_OK</span></span>|<span data-ttu-id="57bb3-111">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="57bb3-111">The operation was successful.</span></span>|  
|<span data-ttu-id="57bb3-112">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="57bb3-112">S_FALSE</span></span>|<span data-ttu-id="57bb3-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="57bb3-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="57bb3-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="57bb3-114">E_FAIL</span></span>|<span data-ttu-id="57bb3-115">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="57bb3-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="57bb3-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="57bb3-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="57bb3-117">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="57bb3-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="57bb3-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="57bb3-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="57bb3-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="57bb3-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="57bb3-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57bb3-120">Requirements</span></span>  
 <span data-ttu-id="57bb3-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57bb3-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57bb3-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="57bb3-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="57bb3-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="57bb3-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="57bb3-124">**Wersja platformy .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="57bb3-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57bb3-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57bb3-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="57bb3-126">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="57bb3-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
