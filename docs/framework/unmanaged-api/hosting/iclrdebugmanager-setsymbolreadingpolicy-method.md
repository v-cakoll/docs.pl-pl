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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969991"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="24426-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="24426-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="24426-103">Ustawia zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="24426-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="24426-104">Zasady określają, czy informacje o numery wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="24426-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24426-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="24426-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24426-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="24426-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="24426-107">[in] Członek [esymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="24426-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24426-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="24426-108">Return Value</span></span>  
  
|<span data-ttu-id="24426-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24426-109">HRESULT</span></span>|<span data-ttu-id="24426-110">Opis</span><span class="sxs-lookup"><span data-stu-id="24426-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24426-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="24426-111">S_OK</span></span>|<span data-ttu-id="24426-112">`SetSymbolReadingPolicy` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="24426-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="24426-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24426-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24426-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="24426-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24426-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24426-115">E_FAIL</span></span>|<span data-ttu-id="24426-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="24426-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24426-117">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="24426-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24426-118">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="24426-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24426-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24426-119">Requirements</span></span>  
 <span data-ttu-id="24426-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24426-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24426-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="24426-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24426-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24426-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24426-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24426-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24426-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24426-124">See also</span></span>

- [<span data-ttu-id="24426-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="24426-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
