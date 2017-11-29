---
title: "LPTHREAD_START_ROUTINE — Wskaźnik funkcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LPTHREAD_START_ROUTINE
api_location: mscoree.dll
api_type: COM
f1_keywords: LPTHREAD_START_ROUTINE
helpviewer_keywords: LPTHREAD_START_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 7b9b93b0-fe92-42ba-8693-701168a29dde
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f29e4e52f9629073d676903e3f828a84023065bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="lpthreadstartroutine-function-pointer"></a><span data-ttu-id="d6482-102">LPTHREAD_START_ROUTINE — Wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="d6482-102">LPTHREAD_START_ROUTINE Function Pointer</span></span>
<span data-ttu-id="d6482-103">Punkty funkcji, które powiadamia hosta, który wątek został uruchomiony w trybie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d6482-103">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 <span data-ttu-id="d6482-104">This, wskaźnik funkcji jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6482-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6482-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6482-105">Syntax</span></span>  
  
```  
typedef DWORD (__stdcall *LPTHREAD_START_ROUTINE) (  
    [in] LPVOID lpThreadParameter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6482-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="d6482-106">Parameters</span></span>  
 `lpThreadParameter`  
 <span data-ttu-id="d6482-107">[in] Wskaźnik do kodu, który rozpoczęła wykonywanie zadania.</span><span class="sxs-lookup"><span data-stu-id="d6482-107">[in] A pointer to the code that has started executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6482-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6482-108">Remarks</span></span>  
 <span data-ttu-id="d6482-109">Funkcja, do której `LPTHREAD_START_ROUTINE` punktów jest funkcją wywołania zwrotnego i musi być implementowana przez Edytor hostingu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d6482-109">The function to which `LPTHREAD_START_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6482-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d6482-110">Requirements</span></span>  
 <span data-ttu-id="d6482-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6482-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6482-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d6482-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6482-113">**Biblioteka:** Mscorwks.dll.a;a;pierwsza</span><span class="sxs-lookup"><span data-stu-id="d6482-113">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d6482-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6482-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6482-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6482-115">See Also</span></span>  
 [<span data-ttu-id="d6482-116">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="d6482-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
