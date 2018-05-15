---
title: ICorRuntimeHost::Stop — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1aea8cb4c180477fdd763a8af2f251db2d37d066
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="43053-102">ICorRuntimeHost::Stop — Metoda</span><span class="sxs-lookup"><span data-stu-id="43053-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="43053-103">Zatrzymuje wykonywanie kodu w czasie wykonywania dla bieżącego procesu.</span><span class="sxs-lookup"><span data-stu-id="43053-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43053-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43053-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="43053-105">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="43053-105">Return Value</span></span>  
  
|<span data-ttu-id="43053-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43053-106">HRESULT</span></span>|<span data-ttu-id="43053-107">Opis</span><span class="sxs-lookup"><span data-stu-id="43053-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43053-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="43053-108">S_OK</span></span>|<span data-ttu-id="43053-109">Operacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="43053-109">The operation was successful.</span></span>|  
|<span data-ttu-id="43053-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="43053-110">S_FALSE</span></span>|<span data-ttu-id="43053-111">Nie można ukończyć operacji.</span><span class="sxs-lookup"><span data-stu-id="43053-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="43053-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43053-112">E_FAIL</span></span>|<span data-ttu-id="43053-113">Wystąpił nieznany, poważnej awarii.</span><span class="sxs-lookup"><span data-stu-id="43053-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="43053-114">Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie.</span><span class="sxs-lookup"><span data-stu-id="43053-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="43053-115">Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="43053-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="43053-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43053-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43053-117">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="43053-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43053-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43053-118">Remarks</span></span>  
 <span data-ttu-id="43053-119">Zwykle nie trzeba wywołać `Stop` metody, ponieważ kod zatrzymuje wykonywanie, gdy kończy proces.</span><span class="sxs-lookup"><span data-stu-id="43053-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43053-120">Po wywołaniu `Stop`, CLR nie można ponownie zainicjować do tego samego procesu.</span><span class="sxs-lookup"><span data-stu-id="43053-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43053-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43053-121">Requirements</span></span>  
 <span data-ttu-id="43053-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43053-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43053-123">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="43053-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43053-124">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43053-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43053-125">**Wersje programu .NET framework:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="43053-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43053-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43053-126">See Also</span></span>  
 [<span data-ttu-id="43053-127">ICorRuntimeHost, interfejs</span><span class="sxs-lookup"><span data-stu-id="43053-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
