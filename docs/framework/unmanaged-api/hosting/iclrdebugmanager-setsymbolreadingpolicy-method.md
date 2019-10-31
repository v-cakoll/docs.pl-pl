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
ms.openlocfilehash: 6737b953f39c1087d01f3fb864d84340a6968aba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129353"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="29dbe-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="29dbe-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="29dbe-103">Ustawia zasady odczytywania plików bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="29dbe-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="29dbe-104">Zasady określają, czy informacje o numerach wierszy i plikach są zawarte w stosach wywołań.</span><span class="sxs-lookup"><span data-stu-id="29dbe-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29dbe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="29dbe-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29dbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="29dbe-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="29dbe-107">podczas Element członkowski wyliczenia [ESymbolReadingPolicy —](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="29dbe-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29dbe-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="29dbe-108">Return Value</span></span>  
  
|<span data-ttu-id="29dbe-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29dbe-109">HRESULT</span></span>|<span data-ttu-id="29dbe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="29dbe-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29dbe-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="29dbe-111">S_OK</span></span>|<span data-ttu-id="29dbe-112">`SetSymbolReadingPolicy` pomyślnie zwrócone.</span><span class="sxs-lookup"><span data-stu-id="29dbe-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="29dbe-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="29dbe-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="29dbe-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="29dbe-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="29dbe-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="29dbe-115">E_FAIL</span></span>|<span data-ttu-id="29dbe-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="29dbe-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="29dbe-117">Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="29dbe-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="29dbe-118">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="29dbe-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29dbe-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29dbe-119">Requirements</span></span>  
 <span data-ttu-id="29dbe-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dbe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dbe-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="29dbe-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="29dbe-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="29dbe-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29dbe-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dbe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29dbe-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29dbe-124">See also</span></span>

- [<span data-ttu-id="29dbe-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="29dbe-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
