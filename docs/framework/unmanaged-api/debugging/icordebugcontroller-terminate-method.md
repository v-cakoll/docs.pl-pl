---
title: "ICorDebugController::Terminate — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Terminate
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb3831e2640de8ad34299695b571cb4071974bd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="45af5-102">ICorDebugController::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="45af5-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="45af5-103">Kończy proces o określony kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="45af5-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45af5-104">Ta metoda jest otoki dla środowiska Win32 `TerminateProcess` funkcji.</span><span class="sxs-lookup"><span data-stu-id="45af5-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="45af5-105">W związku z tym `Terminate` używa kod zakończenia w taki sam jak robi Win32 `TerminateProcess` funkcja używa jej.</span><span class="sxs-lookup"><span data-stu-id="45af5-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45af5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="45af5-106">Syntax</span></span>  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45af5-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="45af5-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="45af5-108">[in] Wartość liczbowa jest kod wyjścia.</span><span class="sxs-lookup"><span data-stu-id="45af5-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="45af5-109">Prawidłowe wartości liczbowe są definiowane w Winbase.h.</span><span class="sxs-lookup"><span data-stu-id="45af5-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45af5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45af5-110">Remarks</span></span>  
 <span data-ttu-id="45af5-111">Jeśli proces zostanie zatrzymana, gdy `Terminate` jest wywoływana, proces powinno być kontynuowane przy użyciu [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) — metoda tak, aby debuger odbiera potwierdzenie Kończenie działania za pomocą [ ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="45af5-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45af5-112">Ta metoda nie jest zaimplementowana przez domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45af5-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="45af5-113">Oznacza to, że nie jest zaimplementowana w <xref:System.AppDomain> poziom.</span><span class="sxs-lookup"><span data-stu-id="45af5-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45af5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45af5-114">Requirements</span></span>  
 <span data-ttu-id="45af5-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45af5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45af5-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45af5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45af5-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45af5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45af5-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45af5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45af5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45af5-119">See Also</span></span>  
 
