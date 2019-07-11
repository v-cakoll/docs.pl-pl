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
ms.openlocfilehash: 65af5303468904ee40da4d567381782af70bfb38
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776499"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="dc0a0-102">WAITORTIMERCALLBACK — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="dc0a0-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="dc0a0-103">Wskazuje funkcję, która powiadamia hosta, którego obsługa oczekiwania (<xref:System.Threading.WaitHandle>) zostały zasygnalizowane lub przekroczyło limit czasu.</span><span class="sxs-lookup"><span data-stu-id="dc0a0-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="dc0a0-104">Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dc0a0-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc0a0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc0a0-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc0a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc0a0-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="dc0a0-107">[in] Wskaźnik do obiektu, który zawiera informacje o zdefiniowanym przez hosta.</span><span class="sxs-lookup"><span data-stu-id="dc0a0-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="dc0a0-108">[in] `true` Jeśli dojście oczekiwania upłynął limit czasu, lub `false` Jeśli został on zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="dc0a0-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc0a0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc0a0-109">Remarks</span></span>  
 <span data-ttu-id="dc0a0-110">Funkcja, do którego `WAITORTIMERCALLBACK` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="dc0a0-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc0a0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc0a0-111">Requirements</span></span>  
 <span data-ttu-id="dc0a0-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc0a0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc0a0-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc0a0-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc0a0-114">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="dc0a0-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="dc0a0-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc0a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc0a0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dc0a0-116">See also</span></span>

- [<span data-ttu-id="dc0a0-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="dc0a0-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
