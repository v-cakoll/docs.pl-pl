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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072860"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="541fb-102">ICorRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="541fb-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="541fb-103">Uruchamia środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="541fb-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="541fb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="541fb-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="541fb-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="541fb-105">Return Value</span></span>  
  
|<span data-ttu-id="541fb-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="541fb-106">HRESULT</span></span>|<span data-ttu-id="541fb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="541fb-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="541fb-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="541fb-108">S_OK</span></span>|<span data-ttu-id="541fb-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="541fb-109">The operation was successful.</span></span>|  
|<span data-ttu-id="541fb-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="541fb-110">S_FALSE</span></span>|<span data-ttu-id="541fb-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="541fb-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="541fb-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="541fb-112">E_FAIL</span></span>|<span data-ttu-id="541fb-113">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="541fb-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="541fb-114">Jeśli metoda zwraca E_FAIL, środowisko CLR nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="541fb-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="541fb-115">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="541fb-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="541fb-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="541fb-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="541fb-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="541fb-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541fb-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="541fb-118">Remarks</span></span>  
 <span data-ttu-id="541fb-119">Zazwyczaj nie jest konieczne wywołać `Start` metody, ponieważ środowisko CLR jest uruchamiany automatycznie po pierwsze żądanie do uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="541fb-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="541fb-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="541fb-120">Requirements</span></span>  
 <span data-ttu-id="541fb-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="541fb-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="541fb-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="541fb-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="541fb-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="541fb-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="541fb-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="541fb-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541fb-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="541fb-125">See also</span></span>

- [<span data-ttu-id="541fb-126">ICorRuntimeHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="541fb-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
