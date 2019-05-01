---
title: ICorRuntimeHost::GetDefaultDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41a6c5ee73cad77368e83792d11d455d8fb163fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937036"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="14a1b-102">ICorRuntimeHost::GetDefaultDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="14a1b-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="14a1b-103">Pobiera wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domyślnej domeny dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="14a1b-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="14a1b-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14a1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14a1b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="14a1b-106">[out] Wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> do <xref:System.AppDomain> wystąpienia, która reprezentuje domyślnej domeny aplikacji dla procesu.</span><span class="sxs-lookup"><span data-stu-id="14a1b-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="14a1b-107">This, wskaźnik jest wpisane `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` uzyskać wskaźnika interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="14a1b-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14a1b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="14a1b-108">Return Value</span></span>  
  
|<span data-ttu-id="14a1b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="14a1b-109">HRESULT</span></span>|<span data-ttu-id="14a1b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="14a1b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="14a1b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="14a1b-111">S_OK</span></span>|<span data-ttu-id="14a1b-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="14a1b-112">The operation was successful.</span></span>|  
|<span data-ttu-id="14a1b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="14a1b-113">S_FALSE</span></span>|<span data-ttu-id="14a1b-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="14a1b-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="14a1b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="14a1b-115">E_FAIL</span></span>|<span data-ttu-id="14a1b-116">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="14a1b-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="14a1b-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="14a1b-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="14a1b-118">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="14a1b-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="14a1b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="14a1b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="14a1b-120">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="14a1b-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="14a1b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="14a1b-121">Requirements</span></span>  
 <span data-ttu-id="14a1b-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a1b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a1b-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="14a1b-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="14a1b-124">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="14a1b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="14a1b-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="14a1b-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a1b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14a1b-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="14a1b-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="14a1b-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
