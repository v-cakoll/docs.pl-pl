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
ms.openlocfilehash: d116883c39b4400451ede07df83ac77893ce285c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="f00d3-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="f00d3-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="f00d3-103">Ustawia zasady do odczytywania plików programu (PDB) bazy danych.</span><span class="sxs-lookup"><span data-stu-id="f00d3-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="f00d3-104">Zasady określa, czy informacje dotyczące numerów wierszy i pliki są uwzględniane w stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="f00d3-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f00d3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f00d3-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f00d3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f00d3-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="f00d3-107">[in] Członek [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="f00d3-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f00d3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f00d3-108">Return Value</span></span>  
  
|<span data-ttu-id="f00d3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f00d3-109">HRESULT</span></span>|<span data-ttu-id="f00d3-110">Opis</span><span class="sxs-lookup"><span data-stu-id="f00d3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f00d3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f00d3-111">S_OK</span></span>|<span data-ttu-id="f00d3-112">`SetSymbolReadingPolicy`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f00d3-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="f00d3-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f00d3-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f00d3-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="f00d3-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f00d3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f00d3-115">E_FAIL</span></span>|<span data-ttu-id="f00d3-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="f00d3-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f00d3-117">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="f00d3-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f00d3-118">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f00d3-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f00d3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f00d3-119">Requirements</span></span>  
 <span data-ttu-id="f00d3-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f00d3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f00d3-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f00d3-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f00d3-122">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f00d3-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f00d3-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f00d3-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f00d3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f00d3-124">See Also</span></span>  
 [<span data-ttu-id="f00d3-125">ICLRDebugManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="f00d3-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
