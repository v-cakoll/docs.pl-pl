---
title: ICorRuntimeHost::CreateDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea63627bc1e689c93634c8fe8b9048b271758573
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937051"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="e0a33-102">ICorRuntimeHost::CreateDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0a33-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="e0a33-103">Tworzy domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e0a33-103">Creates an application domain.</span></span> <span data-ttu-id="e0a33-104">Obiekt wywołujący otrzymuje wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0a33-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0a33-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0a33-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0a33-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0a33-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="e0a33-107">[in] Opcjonalny parametr umożliwia oferowanie przyjazną nazwę domeny.</span><span class="sxs-lookup"><span data-stu-id="e0a33-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="e0a33-108">Ta przyjazna nazwa może wyświetlana w interfejsie użytkownika, takich jak debugery do identyfikowania domeny.</span><span class="sxs-lookup"><span data-stu-id="e0a33-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="e0a33-109">[in] Opcjonalną tablicę wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń, aby ustanowić zestaw uprawnień.</span><span class="sxs-lookup"><span data-stu-id="e0a33-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="e0a33-110">`IIdentity` Obiektu można uzyskać przez wywołanie metody [createevidence —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e0a33-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="e0a33-111">[out] Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> można jeszcze bardziej kontrolować domeny.</span><span class="sxs-lookup"><span data-stu-id="e0a33-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0a33-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0a33-112">Return Value</span></span>  
  
|<span data-ttu-id="e0a33-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e0a33-113">HRESULT</span></span>|<span data-ttu-id="e0a33-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e0a33-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e0a33-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="e0a33-115">S_OK</span></span>|<span data-ttu-id="e0a33-116">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e0a33-116">The operation was successful.</span></span>|  
|<span data-ttu-id="e0a33-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="e0a33-117">S_FALSE</span></span>|<span data-ttu-id="e0a33-118">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="e0a33-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="e0a33-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e0a33-119">E_FAIL</span></span>|<span data-ttu-id="e0a33-120">Wystąpił błąd nieznanego, krytycznego.</span><span class="sxs-lookup"><span data-stu-id="e0a33-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="e0a33-121">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie.</span><span class="sxs-lookup"><span data-stu-id="e0a33-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="e0a33-122">Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e0a33-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e0a33-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e0a33-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e0a33-124">Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="e0a33-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e0a33-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0a33-125">Requirements</span></span>  
 <span data-ttu-id="e0a33-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0a33-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0a33-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0a33-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0a33-128">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e0a33-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0a33-129">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="e0a33-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0a33-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0a33-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="e0a33-131">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0a33-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
