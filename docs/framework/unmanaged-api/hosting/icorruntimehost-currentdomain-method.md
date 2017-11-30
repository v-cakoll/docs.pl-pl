---
title: "ICorRuntimeHost::CurrentDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CurrentDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 592b604f5e873f479f2e0489144240c3f021c270
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="1a248-102">ICorRuntimeHost::CurrentDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a248-102">ICorRuntimeHost::CurrentDomain Method</span></span>
<span data-ttu-id="1a248-103">Pobiera wskaźnika interfejsu typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący domeny załadowany w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="1a248-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a248-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a248-104">Syntax</span></span>  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1a248-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a248-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="1a248-106">[out] Wskaźnik typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący wątku bieżącej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a248-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="1a248-107">Ten wskaźnik jest typu `IUnknown`, dlatego zazwyczaj powinny wywoływać elementy wywołujące `QueryInterface` uzyskać wskaźnika typu <xref:System._AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1a248-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a248-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a248-108">Return Value</span></span>  
  
|<span data-ttu-id="1a248-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1a248-109">HRESULT</span></span>|<span data-ttu-id="1a248-110">Opis</span><span class="sxs-lookup"><span data-stu-id="1a248-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1a248-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="1a248-111">S_OK</span></span>|<span data-ttu-id="1a248-112">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="1a248-112">The operation was successful.</span></span>|  
|<span data-ttu-id="1a248-113">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="1a248-113">S_FALSE</span></span>|<span data-ttu-id="1a248-114">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="1a248-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="1a248-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1a248-115">E_FAIL</span></span>|<span data-ttu-id="1a248-116">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="1a248-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="1a248-117">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="1a248-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="1a248-118">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1a248-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1a248-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1a248-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1a248-120">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1a248-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a248-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a248-121">Requirements</span></span>  
 <span data-ttu-id="1a248-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a248-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a248-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1a248-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1a248-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a248-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1a248-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1a248-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a248-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a248-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="1a248-127">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="1a248-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
