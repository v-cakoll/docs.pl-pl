---
title: ICorRuntimeHost::CurrentDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3aa6bc844d2c6629085b0596127c0b51b99357d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766354"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="93b0d-102">ICorRuntimeHost::CurrentDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="93b0d-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="93b0d-103">Pobiera wskaźnik interfejsu typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący domeny załadowany w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="93b0d-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93b0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93b0d-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93b0d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93b0d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="93b0d-106">[out] Wskaźnik typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący wątku bieżącej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="93b0d-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="93b0d-107">This, wskaźnik jest wpisane `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` uzyskać wskaźnika typu <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="93b0d-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93b0d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93b0d-108">Return Value</span></span>  
  
|<span data-ttu-id="93b0d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="93b0d-109">HRESULT</span></span>|<span data-ttu-id="93b0d-110">Opis</span><span class="sxs-lookup"><span data-stu-id="93b0d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93b0d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="93b0d-111">S_OK</span></span>|<span data-ttu-id="93b0d-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="93b0d-112">The operation was successful.</span></span>|  
|<span data-ttu-id="93b0d-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="93b0d-113">S_FALSE</span></span>|<span data-ttu-id="93b0d-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="93b0d-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="93b0d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="93b0d-115">E_FAIL</span></span>|<span data-ttu-id="93b0d-116">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="93b0d-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="93b0d-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="93b0d-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="93b0d-118">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="93b0d-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="93b0d-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="93b0d-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="93b0d-120">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="93b0d-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93b0d-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93b0d-121">Requirements</span></span>  
 <span data-ttu-id="93b0d-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93b0d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93b0d-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="93b0d-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="93b0d-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="93b0d-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="93b0d-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="93b0d-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93b0d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93b0d-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="93b0d-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="93b0d-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
