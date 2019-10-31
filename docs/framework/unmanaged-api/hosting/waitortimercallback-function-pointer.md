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
ms.openlocfilehash: db6a20dee21b6c8bbd55fa9b52a159a00fe310d5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092036"
---
# <a name="waitortimercallback-function-pointer"></a><span data-ttu-id="f146f-102">WAITORTIMERCALLBACK — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="f146f-102">WAITORTIMERCALLBACK Function Pointer</span></span>
<span data-ttu-id="f146f-103">Wskazuje funkcję, która powiadamia hosta o zasygnalizowaniu lub przekroczeniu limitu czasu dojścia oczekiwania (<xref:System.Threading.WaitHandle>).</span><span class="sxs-lookup"><span data-stu-id="f146f-103">Points to a function that notifies the host that a wait handle (<xref:System.Threading.WaitHandle>) has either been signaled or timed out.</span></span>  
  
 <span data-ttu-id="f146f-104">Ten wskaźnik funkcji został uznany za przestarzały w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="f146f-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f146f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f146f-105">Syntax</span></span>  
  
```cpp  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f146f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="f146f-106">Parameters</span></span>  
 `lpParameter`  
 <span data-ttu-id="f146f-107">podczas Wskaźnik do obiektu, który zawiera informacje zdefiniowane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="f146f-107">[in] A pointer to an object that contains information defined by the host.</span></span>  
  
 `TimerOrWaitFired`  
 <span data-ttu-id="f146f-108">[in] `true`, jeśli upłynął limit czasu dojścia oczekiwania lub `false`, jeśli został zasygnalizowani.</span><span class="sxs-lookup"><span data-stu-id="f146f-108">[in] `true` if the wait handle timed out, or `false` if it was signaled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f146f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f146f-109">Remarks</span></span>  
 <span data-ttu-id="f146f-110">Funkcja, do której punkty `WAITORTIMERCALLBACK` są funkcją wywołania zwrotnego i musi być implementowana przez moduł zapisujący aplikacji hostingowej.</span><span class="sxs-lookup"><span data-stu-id="f146f-110">The function to which `WAITORTIMERCALLBACK` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f146f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f146f-111">Requirements</span></span>  
 <span data-ttu-id="f146f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f146f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f146f-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f146f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f146f-114">**Biblioteka:** MSCorWks. dll</span><span class="sxs-lookup"><span data-stu-id="f146f-114">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="f146f-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f146f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f146f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f146f-116">See also</span></span>

- [<span data-ttu-id="f146f-117">Przestarzałe funkcje hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="f146f-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
