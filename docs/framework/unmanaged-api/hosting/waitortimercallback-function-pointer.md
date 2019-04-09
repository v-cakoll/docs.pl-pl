---
title: WAITORTIMERCALLBACK — Wskaźnik funkcji
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8cf12fc6828c5e439a6a86532f22b8a598a9f03
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120994"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="dfabd-102">WAITORTIMERCALLBACK — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="dfabd-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="dfabd-103">Wskazuje funkcję, która powiadamia hosta, którego obsługa oczekiwania (<xref:System.Threading.WaitHandle>) zostały zasygnalizowane lub przekroczyło limit czasu.</span><span class="sxs-lookup"><span data-stu-id="dfabd-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="dfabd-104">Ten wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfabd-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfabd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dfabd-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfabd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfabd-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="dfabd-107">[in] Wskaźnik do obiektu, który zawiera informacje o zdefiniowanym przez hosta.</span><span class="sxs-lookup"><span data-stu-id="dfabd-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="dfabd-108">[in] `true` Jeśli dojście oczekiwania upłynął limit czasu, lub `false` Jeśli został on zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="dfabd-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfabd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dfabd-109">Remarks</span></span>  
 <span data-ttu-id="dfabd-110">Funkcja, do którego `WAITORTIMERCALLBACK` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="dfabd-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfabd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dfabd-111">Requirements</span></span>  
 <span data-ttu-id="dfabd-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfabd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfabd-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfabd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfabd-114">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="dfabd-114">**Library:** MSCorWks.dll</span></span>  
  
 **<span data-ttu-id="dfabd-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dfabd-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dfabd-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfabd-116">See also</span></span>

- [<span data-ttu-id="dfabd-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dfabd-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
