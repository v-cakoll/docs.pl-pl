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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ed1db49be78d7d16648a9ef9735e79ef1b3ab98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698203"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="c65cf-102">GetStartupNotificationEvent — Funkcja</span><span class="sxs-lookup"><span data-stu-id="c65cf-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="c65cf-103">Tworzy lub zostanie otwarte dojście zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie docelowym określonym.</span><span class="sxs-lookup"><span data-stu-id="c65cf-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65cf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c65cf-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c65cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c65cf-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="c65cf-106">[in] Proces identyfikator procesu docelowego, z którego będą otrzymywać powiadomienia o uruchamiania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="c65cf-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="c65cf-107">[out] Wskaźnik do uchwytu, który zostanie zasygnalizowane przez CLR podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="c65cf-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c65cf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c65cf-108">Return Value</span></span>  
 <span data-ttu-id="c65cf-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="c65cf-109">S_OK</span></span>  
 <span data-ttu-id="c65cf-110">Pomyślnie uzyskano dojścia do uruchamiania zdarzenie powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="c65cf-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="c65cf-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c65cf-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="c65cf-112">`phStartupEvent` ma wartość null lub `debuggeePID` nie odwołuje się do procesu, który jest obecnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="c65cf-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="c65cf-113">E_FAIL (lub inne kody powrotne e_)</span><span class="sxs-lookup"><span data-stu-id="c65cf-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="c65cf-114">Nie można uzyskać dojścia do uruchamiania zdarzenie powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="c65cf-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c65cf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c65cf-115">Remarks</span></span>  
 <span data-ttu-id="c65cf-116">W systemie operacyjnym Windows `debuggeePID` mapuje do systemu operacyjnego przetworzyć identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="c65cf-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="c65cf-117">Zdarzenie jest sygnalizowane przed każdą zarządzane, że kod jest wykonywany przez środowisko CLR, która jest sygnalizowane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c65cf-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65cf-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c65cf-118">Requirements</span></span>  
 <span data-ttu-id="c65cf-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c65cf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c65cf-120">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="c65cf-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c65cf-121">**Biblioteka:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="c65cf-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c65cf-122">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="c65cf-122">**.NET Framework Versions:** 3.5 SP1</span></span>
