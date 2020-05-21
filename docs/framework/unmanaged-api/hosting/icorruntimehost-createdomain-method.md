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
ms.openlocfilehash: 74f17c77e74edb1226dda2d9ebaa9486e1769ce4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762360"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="37ee1-102">ICorRuntimeHost::CreateDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="37ee1-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="37ee1-103">Tworzy domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="37ee1-103">Creates an application domain.</span></span> <span data-ttu-id="37ee1-104">Obiekt wywołujący otrzymuje wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="37ee1-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37ee1-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="37ee1-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37ee1-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="37ee1-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="37ee1-107">podczas Opcjonalny parametr używany do nadawania przyjaznej nazwy do domeny.</span><span class="sxs-lookup"><span data-stu-id="37ee1-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="37ee1-108">Ta przyjazna nazwa może być wyświetlana w interfejsach użytkownika, takich jak debugery, aby identyfikować domenę.</span><span class="sxs-lookup"><span data-stu-id="37ee1-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="37ee1-109">podczas Opcjonalna tablica wskaźników do `IIdentity` wystąpień, które reprezentują dowody mapowane za pomocą zasad zabezpieczeń w celu ustanowienia zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="37ee1-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="37ee1-110">`IIdentity`Obiekt można uzyskać przez wywołanie metody. [CreateEvidence](icorruntimehost-createevidence-method.md)</span><span class="sxs-lookup"><span data-stu-id="37ee1-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="37ee1-111">określoną Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> , które może służyć do dalszej kontroli nad domeną.</span><span class="sxs-lookup"><span data-stu-id="37ee1-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37ee1-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="37ee1-112">Return Value</span></span>  
  
|<span data-ttu-id="37ee1-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37ee1-113">HRESULT</span></span>|<span data-ttu-id="37ee1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="37ee1-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37ee1-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="37ee1-115">S_OK</span></span>|<span data-ttu-id="37ee1-116">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37ee1-116">The operation was successful.</span></span>|  
|<span data-ttu-id="37ee1-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="37ee1-117">S_FALSE</span></span>|<span data-ttu-id="37ee1-118">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="37ee1-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="37ee1-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37ee1-119">E_FAIL</span></span>|<span data-ttu-id="37ee1-120">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="37ee1-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="37ee1-121">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="37ee1-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="37ee1-122">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37ee1-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="37ee1-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37ee1-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37ee1-124">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37ee1-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="37ee1-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37ee1-125">Requirements</span></span>  
 <span data-ttu-id="37ee1-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37ee1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37ee1-127">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37ee1-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37ee1-128">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37ee1-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37ee1-129">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="37ee1-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37ee1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37ee1-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="37ee1-131">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="37ee1-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
