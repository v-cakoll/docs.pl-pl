---
title: "ICorRuntimeHost::CloseEnum — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b44797f6efaf8904e3df876e9278a977c912ac6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="2670a-102">ICorRuntimeHost::CloseEnum — Metoda</span><span class="sxs-lookup"><span data-stu-id="2670a-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="2670a-103">Resetuje wyliczający domeny na początku listy domen.</span><span class="sxs-lookup"><span data-stu-id="2670a-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2670a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2670a-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2670a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2670a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="2670a-106">[in] Moduł wyliczający, aby zresetować.</span><span class="sxs-lookup"><span data-stu-id="2670a-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2670a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2670a-107">Return Value</span></span>  
  
|<span data-ttu-id="2670a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2670a-108">HRESULT</span></span>|<span data-ttu-id="2670a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2670a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2670a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="2670a-110">S_OK</span></span>|<span data-ttu-id="2670a-111">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="2670a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="2670a-112">WARTOŚCI S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2670a-112">S_FALSE</span></span>|<span data-ttu-id="2670a-113">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="2670a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2670a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2670a-114">E_FAIL</span></span>|<span data-ttu-id="2670a-115">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="2670a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2670a-116">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="2670a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2670a-117">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2670a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2670a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2670a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2670a-119">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="2670a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2670a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2670a-120">Requirements</span></span>  
 <span data-ttu-id="2670a-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2670a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2670a-122">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2670a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2670a-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2670a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2670a-124">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="2670a-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2670a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2670a-125">See Also</span></span>  
 [<span data-ttu-id="2670a-126">CorBindToRuntimeEx — funkcja</span><span class="sxs-lookup"><span data-stu-id="2670a-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="2670a-127">ICorRuntimeHost — interfejs</span><span class="sxs-lookup"><span data-stu-id="2670a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
