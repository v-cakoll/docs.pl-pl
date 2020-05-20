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
ms.openlocfilehash: f037e902a9f573023022c81503ea3b987cf6d424
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615762"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="542d7-102">ICLRDebugManager::SetSymbolReadingPolicy — Metoda</span><span class="sxs-lookup"><span data-stu-id="542d7-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="542d7-103">Ustawia zasady odczytywania plików bazy danych programu (PDB).</span><span class="sxs-lookup"><span data-stu-id="542d7-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="542d7-104">Zasady określają, czy informacje o numerach wierszy i plikach są zawarte w stosach wywołań.</span><span class="sxs-lookup"><span data-stu-id="542d7-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542d7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="542d7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="542d7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="542d7-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="542d7-107">podczas Element członkowski wyliczenia [ESymbolReadingPolicy —](esymbolreadingpolicy-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="542d7-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="542d7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="542d7-108">Return Value</span></span>  
  
|<span data-ttu-id="542d7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="542d7-109">HRESULT</span></span>|<span data-ttu-id="542d7-110">Opis</span><span class="sxs-lookup"><span data-stu-id="542d7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="542d7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="542d7-111">S_OK</span></span>|<span data-ttu-id="542d7-112">`SetSymbolReadingPolicy`pomyślnie zwrócono.</span><span class="sxs-lookup"><span data-stu-id="542d7-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="542d7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="542d7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="542d7-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="542d7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="542d7-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="542d7-115">E_FAIL</span></span>|<span data-ttu-id="542d7-116">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="542d7-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="542d7-117">Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie.</span><span class="sxs-lookup"><span data-stu-id="542d7-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="542d7-118">Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="542d7-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="542d7-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="542d7-119">Requirements</span></span>  
 <span data-ttu-id="542d7-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="542d7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="542d7-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="542d7-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="542d7-122">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="542d7-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="542d7-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="542d7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="542d7-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="542d7-124">See also</span></span>

- [<span data-ttu-id="542d7-125">ICLRDebugManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="542d7-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
