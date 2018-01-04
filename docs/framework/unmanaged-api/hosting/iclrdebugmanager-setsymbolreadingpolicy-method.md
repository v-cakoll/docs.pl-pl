---
title: "ICLRDebugManager::SetSymbolReadingPolicy — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 440bab97dc765438758abad3275bb2e4f8051da9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="aa94f-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="aa94f-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="aa94f-103">Ustawia zasady do odczytywania plików programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="aa94f-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="aa94f-104">Zasady określa, czy informacje dotyczące numerów wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="aa94f-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa94f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa94f-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="aa94f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="aa94f-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="aa94f-107">[in] Członek [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="aa94f-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa94f-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="aa94f-108">Return Value</span></span>  
  
|<span data-ttu-id="aa94f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa94f-109">HRESULT</span></span>|<span data-ttu-id="aa94f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="aa94f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa94f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa94f-111">S_OK</span></span>|<span data-ttu-id="aa94f-112">`SetSymbolReadingPolicy`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="aa94f-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="aa94f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa94f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa94f-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="aa94f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa94f-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa94f-115">E_FAIL</span></span>|<span data-ttu-id="aa94f-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="aa94f-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa94f-117">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="aa94f-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa94f-118">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="aa94f-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa94f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="aa94f-119">Requirements</span></span>  
 <span data-ttu-id="aa94f-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa94f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa94f-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="aa94f-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa94f-122">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="aa94f-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa94f-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa94f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa94f-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa94f-124">See Also</span></span>  
 [<span data-ttu-id="aa94f-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="aa94f-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
