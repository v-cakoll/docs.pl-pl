---
title: ICorRuntimeHost::CloseEnum — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfddd1d8f6fed105224cb2294d68f3f0bc016403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762153"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="d1e73-102">ICorRuntimeHost::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1e73-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="d1e73-103">Resetuje wyliczający domeny do początku listy domen.</span><span class="sxs-lookup"><span data-stu-id="d1e73-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e73-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1e73-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1e73-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1e73-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="d1e73-106">[in] Moduł wyliczający do zresetowania.</span><span class="sxs-lookup"><span data-stu-id="d1e73-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1e73-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1e73-107">Return Value</span></span>  
  
|<span data-ttu-id="d1e73-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d1e73-108">HRESULT</span></span>|<span data-ttu-id="d1e73-109">Opis</span><span class="sxs-lookup"><span data-stu-id="d1e73-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d1e73-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d1e73-110">S_OK</span></span>|<span data-ttu-id="d1e73-111">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d1e73-111">The operation was successful.</span></span>|  
|<span data-ttu-id="d1e73-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d1e73-112">S_FALSE</span></span>|<span data-ttu-id="d1e73-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="d1e73-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d1e73-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d1e73-114">E_FAIL</span></span>|<span data-ttu-id="d1e73-115">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="d1e73-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d1e73-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="d1e73-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d1e73-117">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d1e73-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d1e73-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d1e73-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d1e73-119">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="d1e73-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d1e73-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1e73-120">Requirements</span></span>  
 <span data-ttu-id="d1e73-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1e73-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1e73-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d1e73-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1e73-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d1e73-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1e73-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="d1e73-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1e73-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1e73-125">See also</span></span>

- [<span data-ttu-id="d1e73-126">CorBindToRuntimeEx, funkcja</span><span class="sxs-lookup"><span data-stu-id="d1e73-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="d1e73-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1e73-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
