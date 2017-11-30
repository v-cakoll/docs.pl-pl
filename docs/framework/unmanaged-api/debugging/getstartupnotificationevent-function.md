---
title: "GetStartupNotificationEvent — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetStartupNotificationEvent
api_location: dbgshim.dll
api_type: COM
f1_keywords: GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 305350a9186c90af1e8646bc230536dcd2de47cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="ecd1b-102">GetStartupNotificationEvent — Funkcja</span><span class="sxs-lookup"><span data-stu-id="ecd1b-102">GetStartupNotificationEvent Function</span></span>
<span data-ttu-id="ecd1b-103">Tworzy lub otwiera obsługi zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-103">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecd1b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecd1b-104">Syntax</span></span>  
  
```  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ecd1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecd1b-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="ecd1b-106">[in] Identyfikator procesu Proces docelowy, z których chcesz otrzymywać powiadomienia uruchamiania CLR.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-106">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="ecd1b-107">[out] Wskaźnik do uchwytu, które zostanie zgłoszony przez środowisko CLR podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-107">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecd1b-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ecd1b-108">Return Value</span></span>  
 <span data-ttu-id="ecd1b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="ecd1b-109">S_OK</span></span>  
 <span data-ttu-id="ecd1b-110">Pomyślnie uzyskano dojścia do uruchamiania zdarzeń powiadomień.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-110">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="ecd1b-111">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ecd1b-111">E_INVALIDARG</span></span>  
 <span data-ttu-id="ecd1b-112">`phStartupEvent`ma wartość null lub `debuggeePID` nie odwołuje się do procesu, który jest obecnie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-112">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="ecd1b-113">E_FAIL (lub inne kody powrotu E_)</span><span class="sxs-lookup"><span data-stu-id="ecd1b-113">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ecd1b-114">Nie można uzyskać dojścia do uruchamiania zdarzeń powiadomień.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-114">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecd1b-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecd1b-115">Remarks</span></span>  
 <span data-ttu-id="ecd1b-116">W systemie operacyjnym Windows `debuggeePID` identyfikator przetworzyć map do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-116">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="ecd1b-117">Zdarzenie jest sygnalizowane przed każdą zarządzane, że kod jest wykonywany przez środowisko CLR, która sygnalizuje zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ecd1b-117">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecd1b-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecd1b-118">Requirements</span></span>  
 <span data-ttu-id="ecd1b-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecd1b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecd1b-120">**Nagłówek:** dbgshim.h</span><span class="sxs-lookup"><span data-stu-id="ecd1b-120">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ecd1b-121">**Biblioteka:** biblioteki dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="ecd1b-121">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ecd1b-122">**Wersje programu .NET framework:** 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="ecd1b-122">**.NET Framework Versions:** 3.5 SP1</span></span>
