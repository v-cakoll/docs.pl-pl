---
title: ICorDebugModuleBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5ead45c6747cd69a76585c81b1ff6a4801cbb34
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631999"
---
# <a name="icordebugmodulebreakpoint-interface1"></a><span data-ttu-id="5679d-102">ICorDebugModuleBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="5679d-102">ICorDebugModuleBreakpoint Interface1</span></span>
<span data-ttu-id="5679d-103">Zapewnia dostęp do specyficznych modułów.</span><span class="sxs-lookup"><span data-stu-id="5679d-103">Provides access to specific modules.</span></span> <span data-ttu-id="5679d-104">Ten interfejs jest podklasą icordebugbreakpoint — interfejs.</span><span class="sxs-lookup"><span data-stu-id="5679d-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5679d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5679d-105">Methods</span></span>  
  
|<span data-ttu-id="5679d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5679d-106">Method</span></span>|<span data-ttu-id="5679d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5679d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5679d-108">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="5679d-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="5679d-109">Pobiera wskaźnik interfejsu do ICorDebugModule, który odwołuje się moduł, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="5679d-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5679d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5679d-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5679d-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="5679d-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5679d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5679d-112">Requirements</span></span>  
 <span data-ttu-id="5679d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5679d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5679d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5679d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5679d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5679d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5679d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5679d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5679d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5679d-117">See also</span></span>
- [<span data-ttu-id="5679d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5679d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
