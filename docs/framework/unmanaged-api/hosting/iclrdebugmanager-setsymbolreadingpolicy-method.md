---
title: ICLRDebugManager::SetSymbolReadingPolicy — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dc3d350f5c97736b3b65c814a668195aceef2b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132824"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="fac8d-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="fac8d-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="fac8d-103">Ustawia zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="fac8d-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="fac8d-104">Zasady określają, czy informacje o numery wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="fac8d-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fac8d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fac8d-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fac8d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="fac8d-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="fac8d-107">[in] Członek [esymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="fac8d-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fac8d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fac8d-108">Return Value</span></span>  
  
|<span data-ttu-id="fac8d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fac8d-109">HRESULT</span></span>|<span data-ttu-id="fac8d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="fac8d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fac8d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="fac8d-111">S_OK</span></span>|`SetSymbolReadingPolicy` <span data-ttu-id="fac8d-112">pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="fac8d-112">returned successfully.</span></span>|  
|<span data-ttu-id="fac8d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fac8d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fac8d-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="fac8d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fac8d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fac8d-115">E_FAIL</span></span>|<span data-ttu-id="fac8d-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="fac8d-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fac8d-117">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fac8d-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fac8d-118">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fac8d-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fac8d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fac8d-119">Requirements</span></span>  
 <span data-ttu-id="fac8d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fac8d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fac8d-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fac8d-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fac8d-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fac8d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="fac8d-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="fac8d-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fac8d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fac8d-124">See also</span></span>

- [<span data-ttu-id="fac8d-125">ICLRDebugManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fac8d-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
