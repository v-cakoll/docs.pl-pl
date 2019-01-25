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
ms.openlocfilehash: 349f71691e166561d677e0ae792fa12fc5bb1fc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624313"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="1b420-102">ICorRuntimeHost::Start — Metoda</span><span class="sxs-lookup"><span data-stu-id="1b420-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="1b420-103">Uruchamia środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="1b420-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b420-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b420-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1b420-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1b420-105">Return Value</span></span>  
  
|<span data-ttu-id="1b420-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1b420-106">HRESULT</span></span>|<span data-ttu-id="1b420-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1b420-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1b420-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="1b420-108">S_OK</span></span>|<span data-ttu-id="1b420-109">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1b420-109">The operation was successful.</span></span>|  
|<span data-ttu-id="1b420-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1b420-110">S_FALSE</span></span>|<span data-ttu-id="1b420-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="1b420-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1b420-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1b420-112">E_FAIL</span></span>|<span data-ttu-id="1b420-113">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="1b420-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1b420-114">Jeśli metoda zwraca E_FAIL, środowisko CLR nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="1b420-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="1b420-115">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1b420-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1b420-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1b420-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1b420-117">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1b420-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b420-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b420-118">Remarks</span></span>  
 <span data-ttu-id="1b420-119">Zazwyczaj nie jest konieczne wywołać `Start` metody, ponieważ środowisko CLR jest uruchamiany automatycznie po pierwsze żądanie do uruchomienia kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="1b420-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b420-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b420-120">Requirements</span></span>  
 <span data-ttu-id="1b420-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b420-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b420-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1b420-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1b420-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1b420-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b420-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1b420-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b420-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b420-125">See also</span></span>
- [<span data-ttu-id="1b420-126">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1b420-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
