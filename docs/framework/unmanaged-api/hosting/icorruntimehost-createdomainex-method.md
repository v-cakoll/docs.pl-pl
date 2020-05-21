---
title: ICorRuntimeHost::CreateDomainEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762347"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="cc4e0-102">ICorRuntimeHost::CreateDomainEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="cc4e0-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="cc4e0-103">Tworzy domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-103">Creates an application domain.</span></span> <span data-ttu-id="cc4e0-104">Obiekt wywołujący otrzymuje wskaźnik interfejsu, typu <xref:System._AppDomain> , do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cc4e0-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cc4e0-105">Ta metoda umożliwia obiektowi wywołującemu przekazanie wystąpienia IAppDomainSetup — w celu skonfigurowania dodatkowych funkcji zwracanego <xref:System._AppDomain> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc4e0-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cc4e0-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc4e0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cc4e0-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="cc4e0-108">podczas Opcjonalny parametr używany do nadawania przyjaznej nazwy do domeny.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="cc4e0-109">Ta przyjazna nazwa może być wyświetlana w interfejsach użytkownika, takich jak debugery, aby identyfikować domenę.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="cc4e0-110">podczas Opcjonalny wskaźnik interfejsu typu `IAppDomainSetup` , uzyskany przez wywołanie metody [ICorRuntimeHost:: CreateDomainSetup —](icorruntimehost-createdomainsetup-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cc4e0-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="cc4e0-111">podczas Opcjonalna tablica wskaźników do `IIdentity` wystąpień, które reprezentują dowody mapowane za pomocą zasad zabezpieczeń w celu ustanowienia zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="cc4e0-112">`IIdentity`Obiekt można uzyskać przez wywołanie metody. [CreateEvidence](icorruntimehost-createevidence-method.md)</span><span class="sxs-lookup"><span data-stu-id="cc4e0-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="cc4e0-113">określoną Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> , które może służyć do dalszej kontroli nad domeną.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cc4e0-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cc4e0-114">Return Value</span></span>  
  
|<span data-ttu-id="cc4e0-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cc4e0-115">HRESULT</span></span>|<span data-ttu-id="cc4e0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="cc4e0-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cc4e0-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="cc4e0-117">S_OK</span></span>|<span data-ttu-id="cc4e0-118">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-118">The operation was successful.</span></span>|  
|<span data-ttu-id="cc4e0-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cc4e0-119">S_FALSE</span></span>|<span data-ttu-id="cc4e0-120">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cc4e0-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cc4e0-121">E_FAIL</span></span>|<span data-ttu-id="cc4e0-122">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cc4e0-123">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cc4e0-124">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cc4e0-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cc4e0-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cc4e0-126">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc4e0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cc4e0-127">Remarks</span></span>  
 <span data-ttu-id="cc4e0-128">`CreateDomainEx`rozszerza możliwości funkcji CreateInstance [przez](icorruntimehost-createdomain-method.md) umożliwienie obiektowi wywołującemu przekazania do `IAppDomainSetup` wystąpienia z wartościami właściwości w celu skonfigurowania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cc4e0-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc4e0-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cc4e0-129">Requirements</span></span>  
 <span data-ttu-id="cc4e0-130">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc4e0-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc4e0-131">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cc4e0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cc4e0-132">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cc4e0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cc4e0-133">**Wersja .NET Framework:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="cc4e0-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc4e0-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cc4e0-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="cc4e0-135">CreateDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="cc4e0-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="cc4e0-136">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="cc4e0-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
