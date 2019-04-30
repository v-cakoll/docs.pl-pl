---
title: ICorRuntimeHost::Start — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e6521f8013bf92f073ab4b6808871c95ac2802b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700114"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="be124-102">ICorRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="be124-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="be124-103">Uruchamia środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="be124-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be124-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be124-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="be124-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be124-105">Return Value</span></span>  
  
|<span data-ttu-id="be124-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be124-106">HRESULT</span></span>|<span data-ttu-id="be124-107">Opis</span><span class="sxs-lookup"><span data-stu-id="be124-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be124-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="be124-108">S_OK</span></span>|<span data-ttu-id="be124-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="be124-109">The operation was successful.</span></span>|  
|<span data-ttu-id="be124-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="be124-110">S_FALSE</span></span>|<span data-ttu-id="be124-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="be124-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="be124-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be124-112">E_FAIL</span></span>|<span data-ttu-id="be124-113">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="be124-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="be124-114">Jeśli metoda zwraca E_FAIL, środowisko CLR nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="be124-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="be124-115">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="be124-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be124-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be124-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be124-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="be124-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be124-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be124-118">Remarks</span></span>  
 <span data-ttu-id="be124-119">Zazwyczaj nie jest konieczne wywołać `Start` metody, ponieważ środowisko CLR jest uruchamiany automatycznie po pierwsze żądanie do uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="be124-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be124-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be124-120">Requirements</span></span>  
 <span data-ttu-id="be124-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be124-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be124-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be124-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be124-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be124-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be124-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="be124-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be124-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be124-125">See also</span></span>

- [<span data-ttu-id="be124-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="be124-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
