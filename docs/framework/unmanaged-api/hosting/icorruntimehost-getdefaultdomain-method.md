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
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139557"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="dd6de-102">ICorRuntimeHost::GetDefaultDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="dd6de-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="dd6de-103">Pobiera wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType>, który reprezentuje domenę domyślną dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="dd6de-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd6de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd6de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd6de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd6de-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="dd6de-106">określoną Wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> do wystąpienia <xref:System.AppDomain>, które reprezentuje domyślną domenę aplikacji dla procesu.</span><span class="sxs-lookup"><span data-stu-id="dd6de-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="dd6de-107">Ten wskaźnik jest wpisywany `IUnknown`, dlatego obiekty wywołujące powinny na ogół wywołać `QueryInterface`, aby uzyskać wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dd6de-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd6de-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd6de-108">Return Value</span></span>  
  
|<span data-ttu-id="dd6de-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd6de-109">HRESULT</span></span>|<span data-ttu-id="dd6de-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dd6de-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd6de-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd6de-111">S_OK</span></span>|<span data-ttu-id="dd6de-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd6de-112">The operation was successful.</span></span>|  
|<span data-ttu-id="dd6de-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="dd6de-113">S_FALSE</span></span>|<span data-ttu-id="dd6de-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="dd6de-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="dd6de-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd6de-115">E_FAIL</span></span>|<span data-ttu-id="dd6de-116">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="dd6de-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="dd6de-117">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="dd6de-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="dd6de-118">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dd6de-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dd6de-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dd6de-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dd6de-120">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd6de-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd6de-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd6de-121">Requirements</span></span>  
 <span data-ttu-id="dd6de-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd6de-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd6de-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd6de-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd6de-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd6de-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd6de-125">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="dd6de-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd6de-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd6de-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="dd6de-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd6de-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
