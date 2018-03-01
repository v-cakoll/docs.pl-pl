---
title: "WAITORTIMERCALLBACK — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f39c023c6911ca0bcc6b62a562785c069d846d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="22126-102">WAITORTIMERCALLBACK — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="22126-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="22126-103">Wskazuje funkcji, które powiadamia hosta, który obsługiwać oczekiwania (<xref:System.Threading.WaitHandle>) albo został sygnalizowane lub upłynął limit czasu.</span><span class="sxs-lookup"><span data-stu-id="22126-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="22126-104">This, wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="22126-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22126-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="22126-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22126-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="22126-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="22126-107">[in] Wskaźnik do obiektu, który zawiera informacje zdefiniowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="22126-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="22126-108">[in] `true` Jeśli dojście oczekiwania został przekroczony, lub `false` Jeśli został on sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="22126-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22126-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22126-109">Remarks</span></span>  
 <span data-ttu-id="22126-110">Funkcja, do której `WAITORTIMERCALLBACK` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="22126-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22126-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="22126-111">Requirements</span></span>  
 <span data-ttu-id="22126-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22126-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22126-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22126-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22126-114">**Biblioteka:** Mscorwks.dll.a;a;pierwsza</span><span class="sxs-lookup"><span data-stu-id="22126-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="22126-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22126-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22126-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="22126-116">See Also</span></span>  
 [<span data-ttu-id="22126-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="22126-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
