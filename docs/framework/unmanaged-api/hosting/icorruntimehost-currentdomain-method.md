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
ms.openlocfilehash: 38042876cf4397418d2e6e6ed2bfbeb2df2d62d8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762295"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="1246a-102">ICorRuntimeHost::CurrentDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="1246a-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="1246a-103">Pobiera wskaźnik interfejsu typu <xref:System.AppDomain?displayProperty=nameWithType> , który reprezentuje domenę załadowana w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="1246a-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1246a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1246a-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1246a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1246a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1246a-106">określoną Wskaźnik typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący bieżącą domenę aplikacji wątku.</span><span class="sxs-lookup"><span data-stu-id="1246a-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="1246a-107">Ten wskaźnik jest wpisywany `IUnknown` , dlatego obiekty wywołujące powinny na ogół wywołać, `QueryInterface` Aby uzyskać wskaźnik typu <xref:System._AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="1246a-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1246a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1246a-108">Return Value</span></span>  
  
|<span data-ttu-id="1246a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1246a-109">HRESULT</span></span>|<span data-ttu-id="1246a-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1246a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1246a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1246a-111">S_OK</span></span>|<span data-ttu-id="1246a-112">Operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1246a-112">The operation was successful.</span></span>|  
|<span data-ttu-id="1246a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1246a-113">S_FALSE</span></span>|<span data-ttu-id="1246a-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="1246a-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1246a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1246a-115">E_FAIL</span></span>|<span data-ttu-id="1246a-116">Wystąpił nieznany, Katastrofalny błąd.</span><span class="sxs-lookup"><span data-stu-id="1246a-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1246a-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe do użycia w procesie.</span><span class="sxs-lookup"><span data-stu-id="1246a-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1246a-118">Kolejne wywołania interfejsów API hostingu zwracają HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1246a-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1246a-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1246a-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1246a-120">Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1246a-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1246a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1246a-121">Requirements</span></span>  
 <span data-ttu-id="1246a-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1246a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1246a-123">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1246a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1246a-124">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1246a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1246a-125">**.NET Framework wersje:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="1246a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1246a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1246a-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="1246a-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="1246a-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
