---
title: GetStartupNotificationEvent — Funkcja
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: fb158b35165fb229fc78169e2508679b6749752e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122953"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="4bf23-102">GetStartupNotificationEvent — Funkcja</span><span class="sxs-lookup"><span data-stu-id="4bf23-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="4bf23-103">Tworzy lub otwiera dojście zdarzenia, które będzie sygnalizowane przez środowisko uruchomieniowe języka wspólnego (CLR) ładowane w określonym procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="4bf23-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4bf23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bf23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4bf23-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="4bf23-106">podczas Identyfikator procesu docelowego, z którego mają zostać odebrane powiadomienia uruchomieniowe środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="4bf23-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="4bf23-107">określoną Wskaźnik do dojścia, który zostanie zasygnalizowani przez CLR podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="4bf23-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bf23-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4bf23-108">Return Value</span></span>  
 <span data-ttu-id="4bf23-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bf23-109">S_OK</span></span>  
 <span data-ttu-id="4bf23-110">Pomyślnie uzyskano dojście do zdarzenia powiadomienia uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4bf23-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="4bf23-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="4bf23-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="4bf23-112">`phStartupEvent` ma wartość null lub `debuggeePID` nie odwołuje się do procesu, który jest obecnie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="4bf23-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="4bf23-113">E_FAIL (lub inne kody powrotne E_)</span><span class="sxs-lookup"><span data-stu-id="4bf23-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="4bf23-114">Nie można uzyskać dojścia do zdarzenia powiadomienia uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="4bf23-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bf23-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4bf23-115">Remarks</span></span>  
 <span data-ttu-id="4bf23-116">W systemie operacyjnym Windows `debuggeePID` mapuje na identyfikator procesu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="4bf23-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="4bf23-117">Zdarzenie jest sygnalizowane przed wykonaniem kodu zarządzanego przez środowisko CLR sygnalizujące zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4bf23-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf23-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4bf23-118">Requirements</span></span>  
 <span data-ttu-id="4bf23-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf23-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf23-120">**Nagłówek:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="4bf23-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="4bf23-121">**Biblioteka:** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="4bf23-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="4bf23-122">**.NET Framework wersje:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="4bf23-122">**.NET Framework Versions:** 3.5 SP1</span></span>
