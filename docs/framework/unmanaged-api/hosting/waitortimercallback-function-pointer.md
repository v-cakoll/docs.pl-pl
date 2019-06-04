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
ms.openlocfilehash: f938c7dcf08654eef1e2403426eb5c54d6d2a6b3
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490118"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="017a4-102">WAITORTIMERCALLBACK — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="017a4-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="017a4-103">Wskazuje funkcję, która powiadamia hosta, którego obsługa oczekiwania (<xref:System.Threading.WaitHandle>) zostały zasygnalizowane lub przekroczyło limit czasu.</span><span class="sxs-lookup"><span data-stu-id="017a4-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="017a4-104">Ten wskaźnik funkcji jest przestarzała w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="017a4-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="017a4-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="017a4-105">Syntax</span></span>  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="017a4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="017a4-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="017a4-107">[in] Wskaźnik do obiektu, który zawiera informacje o zdefiniowanym przez hosta.</span><span class="sxs-lookup"><span data-stu-id="017a4-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="017a4-108">[in] `true` Jeśli dojście oczekiwania upłynął limit czasu, lub `false` Jeśli został on zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="017a4-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="017a4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="017a4-109">Remarks</span></span>  
 <span data-ttu-id="017a4-110">Funkcja, do którego `WAITORTIMERCALLBACK` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji macierzystej.</span><span class="sxs-lookup"><span data-stu-id="017a4-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="017a4-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="017a4-111">Requirements</span></span>  
 <span data-ttu-id="017a4-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="017a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="017a4-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="017a4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="017a4-114">**Biblioteka:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="017a4-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="017a4-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="017a4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="017a4-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="017a4-116">See also</span></span>

- [<span data-ttu-id="017a4-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="017a4-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
