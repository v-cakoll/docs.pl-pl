---
title: "ICorRuntimeHost::CreateDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fe0adad8397f42716368691abbb1d1c303fced97
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="1560e-102">ICorRuntimeHost::CreateDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="1560e-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="1560e-103">Tworzy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1560e-103">Creates an application domain.</span></span> <span data-ttu-id="1560e-104">Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1560e-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1560e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1560e-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1560e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1560e-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="1560e-107">[in] Parametr opcjonalny używany do nadaj przyjazną nazwę do domeny.</span><span class="sxs-lookup"><span data-stu-id="1560e-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="1560e-108">Przyjazna nazwa mogą być wyświetlane w interfejsów użytkownika, takich jak debugera, aby zidentyfikować domenę.</span><span class="sxs-lookup"><span data-stu-id="1560e-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="1560e-109">[in] Opcjonalne tablicy wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń do ustalenia zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1560e-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="1560e-110">`IIdentity` Obiektu można uzyskać przez wywołanie metody [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="1560e-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="1560e-111">[out] Wskaźnik interfejsu typu <xref:System._AppDomain> na wystąpienie <xref:System.AppDomain?displayProperty=nameWithType> można dodatkowo kontrolować domeny.</span><span class="sxs-lookup"><span data-stu-id="1560e-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1560e-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1560e-112">Return Value</span></span>  
  
|<span data-ttu-id="1560e-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1560e-113">HRESULT</span></span>|<span data-ttu-id="1560e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="1560e-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1560e-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="1560e-115">S_OK</span></span>|<span data-ttu-id="1560e-116">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="1560e-116">The operation was successful.</span></span>|  
|<span data-ttu-id="1560e-117">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1560e-117">S_FALSE</span></span>|<span data-ttu-id="1560e-118">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="1560e-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1560e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1560e-119">E_FAIL</span></span>|<span data-ttu-id="1560e-120">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="1560e-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1560e-121">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1560e-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1560e-122">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1560e-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1560e-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1560e-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1560e-124">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1560e-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1560e-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1560e-125">Requirements</span></span>  
 <span data-ttu-id="1560e-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1560e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1560e-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1560e-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1560e-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1560e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1560e-129">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1560e-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1560e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1560e-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="1560e-131">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1560e-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
