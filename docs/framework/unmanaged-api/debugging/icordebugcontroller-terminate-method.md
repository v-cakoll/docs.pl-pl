---
title: ICorDebugController::Terminate — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06c91a813a80af5cf09914ca134ac9935ed787c8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750070"
---
# <a name="icordebugcontrollerterminate-method"></a><span data-ttu-id="d9288-102">ICorDebugController::Terminate — Metoda</span><span class="sxs-lookup"><span data-stu-id="d9288-102">ICorDebugController::Terminate Method</span></span>
<span data-ttu-id="d9288-103">Kończy proces o określony kod zakończenia.</span><span class="sxs-lookup"><span data-stu-id="d9288-103">Terminates the process with the specified exit code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9288-104">Ta metoda jest otoką Win32 `TerminateProcess` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9288-104">This method is a wrapper for the Win32 `TerminateProcess` function.</span></span> <span data-ttu-id="d9288-105">W związku z tym `Terminate` korzysta z kodem zakończenia w taki sam sposób Win32 `TerminateProcess` używa go w funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9288-105">Thus, `Terminate` uses the exit code in the same way that the Win32 `TerminateProcess` function uses it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9288-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="d9288-106">Syntax</span></span>  
  
```cpp  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9288-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="d9288-107">Parameters</span></span>  
 `exitCode`  
 <span data-ttu-id="d9288-108">[in] Wartość liczbowa jest kod wyjścia.</span><span class="sxs-lookup"><span data-stu-id="d9288-108">[in] A numeric value that is the exit code.</span></span> <span data-ttu-id="d9288-109">Prawidłowe wartości numeryczne są definiowane w Winbase.h.</span><span class="sxs-lookup"><span data-stu-id="d9288-109">The valid numeric values are defined in Winbase.h.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9288-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9288-110">Remarks</span></span>  
 <span data-ttu-id="d9288-111">Jeśli proces zostanie zatrzymany, kiedy `Terminate` jest wywoływana, ten proces należy kontynuować przy użyciu [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody tak, aby debuger odbiera potwierdzenie zakończenia za pośrednictwem [ ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) lub [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d9288-111">If the process is stopped when `Terminate` is called, the process should be continued by using the [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) method so that the debugger receives confirmation of the termination through the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) or [ICorDebugManagedCallback::ExitAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) callback.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9288-112">Ta metoda nie jest zaimplementowana przez domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9288-112">This method is not implemented by an application domain.</span></span> <span data-ttu-id="d9288-113">Oznacza to, że nie jest zaimplementowana w <xref:System.AppDomain> poziom.</span><span class="sxs-lookup"><span data-stu-id="d9288-113">That is, it is not implemented at the <xref:System.AppDomain> level.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9288-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9288-114">Requirements</span></span>  
 <span data-ttu-id="d9288-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9288-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9288-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9288-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9288-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9288-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9288-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9288-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9288-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9288-119">See also</span></span>
