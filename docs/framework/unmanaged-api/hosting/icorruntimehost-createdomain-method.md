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
ms.openlocfilehash: ea2353f1375667619db47ac5e1f037ce68dbded5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="6c330-102">ICorRuntimeHost::CreateDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="6c330-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="6c330-103">Tworzy domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6c330-103">Creates an application domain.</span></span> <span data-ttu-id="6c330-104">Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c330-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c330-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c330-105">Syntax</span></span>  
  
```  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c330-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c330-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="6c330-107">[in] Parametr opcjonalny używany do nadaj przyjazną nazwę do domeny.</span><span class="sxs-lookup"><span data-stu-id="6c330-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="6c330-108">Przyjazna nazwa mogą być wyświetlane w interfejsów użytkownika, takich jak debugera, aby zidentyfikować domenę.</span><span class="sxs-lookup"><span data-stu-id="6c330-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="6c330-109">[in] Opcjonalne tablicy wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń do ustalenia zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="6c330-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="6c330-110">`IIdentity` Obiektu można uzyskać przez wywołanie metody [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6c330-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="6c330-111">[out] Wskaźnik interfejsu typu <xref:System._AppDomain> na wystąpienie <xref:System.AppDomain?displayProperty=nameWithType> można dodatkowo kontrolować domeny.</span><span class="sxs-lookup"><span data-stu-id="6c330-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c330-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6c330-112">Return Value</span></span>  
  
|<span data-ttu-id="6c330-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c330-113">HRESULT</span></span>|<span data-ttu-id="6c330-114">Opis</span><span class="sxs-lookup"><span data-stu-id="6c330-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c330-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c330-115">S_OK</span></span>|<span data-ttu-id="6c330-116">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="6c330-116">The operation was successful.</span></span>|  
|<span data-ttu-id="6c330-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6c330-117">S_FALSE</span></span>|<span data-ttu-id="6c330-118">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="6c330-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6c330-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c330-119">E_FAIL</span></span>|<span data-ttu-id="6c330-120">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="6c330-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6c330-121">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="6c330-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6c330-122">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c330-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6c330-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c330-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c330-124">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="6c330-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6c330-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6c330-125">Requirements</span></span>  
 <span data-ttu-id="6c330-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c330-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c330-127">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c330-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c330-128">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c330-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c330-129">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6c330-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c330-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c330-130">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="6c330-131">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="6c330-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
