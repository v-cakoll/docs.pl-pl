---
title: ICorDebugValueBreakpoint Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fbb0479ee9d14b534e419c74560f4da527884246
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419055"
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="899db-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="899db-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="899db-103">Rozszerzenie interfejsu ICorDebugBreakpoint w celu zapewnienia dostępu do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="899db-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="899db-104">Metody</span><span class="sxs-lookup"><span data-stu-id="899db-104">Methods</span></span>  
  
|<span data-ttu-id="899db-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="899db-105">Method</span></span>|<span data-ttu-id="899db-106">Opis</span><span class="sxs-lookup"><span data-stu-id="899db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="899db-107">GetValue, metoda</span><span class="sxs-lookup"><span data-stu-id="899db-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="899db-108">Pobiera wskaźnika interfejsu do obiektu ICorDebugValue reprezentujący wartość obiektu, na którym jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="899db-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="899db-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="899db-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="899db-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="899db-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="899db-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="899db-111">Requirements</span></span>  
 <span data-ttu-id="899db-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="899db-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="899db-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="899db-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="899db-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="899db-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="899db-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899db-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899db-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="899db-116">See Also</span></span>  
 [<span data-ttu-id="899db-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="899db-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
