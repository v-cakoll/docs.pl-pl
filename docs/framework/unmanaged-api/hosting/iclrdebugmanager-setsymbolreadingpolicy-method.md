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
ms.openlocfilehash: 330501e67e3f19fbdb24c200deacad68de1b6c03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710294"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="f7171-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="f7171-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="f7171-103">Ustawia zasady do odczytywania plików bazy danych (PDB) programu.</span><span class="sxs-lookup"><span data-stu-id="f7171-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="f7171-104">Zasady określają, czy informacje o numery wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="f7171-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7171-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7171-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f7171-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7171-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="f7171-107">[in] Członek [esymbolreadingpolicy —](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f7171-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f7171-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f7171-108">Return Value</span></span>  
  
|<span data-ttu-id="f7171-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7171-109">HRESULT</span></span>|<span data-ttu-id="f7171-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f7171-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f7171-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f7171-111">S_OK</span></span>|<span data-ttu-id="f7171-112">`SetSymbolReadingPolicy` pomyślnie zwrócił.</span><span class="sxs-lookup"><span data-stu-id="f7171-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="f7171-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f7171-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f7171-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f7171-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f7171-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f7171-115">E_FAIL</span></span>|<span data-ttu-id="f7171-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f7171-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f7171-117">Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f7171-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f7171-118">Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f7171-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7171-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7171-119">Requirements</span></span>  
 <span data-ttu-id="f7171-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7171-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7171-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f7171-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f7171-122">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f7171-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f7171-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7171-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7171-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7171-124">See also</span></span>
- [<span data-ttu-id="f7171-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f7171-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
