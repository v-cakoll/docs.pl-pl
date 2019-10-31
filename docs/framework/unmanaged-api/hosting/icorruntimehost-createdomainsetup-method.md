---
title: ICorRuntimeHost::CreateDomainSetup — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139648"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="98d3e-102">ICorRuntimeHost::CreateDomainSetup — Metoda</span><span class="sxs-lookup"><span data-stu-id="98d3e-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="98d3e-103">Pobiera wskaźnik interfejsu typu IAppDomainSetup — do wystąpienia <xref:System.AppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98d3e-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="98d3e-104">`IAppDomainSetup` udostępnia metody konfigurowania aspektów domeny aplikacji przed jej utworzeniem.</span><span class="sxs-lookup"><span data-stu-id="98d3e-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98d3e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="98d3e-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98d3e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="98d3e-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="98d3e-107">określoną Wskaźnik interfejsu do wystąpienia <xref:System.AppDomainSetup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98d3e-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="98d3e-108">Ten parametr jest wpisywany jako `IUnknown`, dlatego obiekty wywołujące powinny na ogół wywołać `QueryInterface` na tym wskaźniku, aby uzyskać wskaźnik interfejsu typu `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="98d3e-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98d3e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="98d3e-109">Return Value</span></span>  
  
|<span data-ttu-id="98d3e-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="98d3e-110">HRESULT</span></span>|<span data-ttu-id="98d3e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="98d3e-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98d3e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="98d3e-112">S_OK</span></span>|<span data-ttu-id="98d3e-113">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98d3e-113">The operation was successful.</span></span>|  
|<span data-ttu-id="98d3e-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="98d3e-114">S_FALSE</span></span>|<span data-ttu-id="98d3e-115">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="98d3e-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="98d3e-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="98d3e-116">E_FAIL</span></span>|<span data-ttu-id="98d3e-117">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="98d3e-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="98d3e-118">Jeśli metoda zwraca wartość E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="98d3e-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="98d3e-119">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="98d3e-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="98d3e-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="98d3e-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="98d3e-121">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98d3e-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98d3e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98d3e-122">Remarks</span></span>  
 <span data-ttu-id="98d3e-123">Wskaźnik zwrócony z tej metody jest zwykle przekazana jako parametr do metody [CreateDomainEx —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98d3e-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98d3e-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98d3e-124">Requirements</span></span>  
 <span data-ttu-id="98d3e-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98d3e-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98d3e-126">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98d3e-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98d3e-127">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="98d3e-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98d3e-128">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="98d3e-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98d3e-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98d3e-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="98d3e-130">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="98d3e-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
