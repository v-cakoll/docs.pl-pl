---
title: ICorDebugValueBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValueBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValueBreakpoint
helpviewer_keywords: ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 04ce1827bbc70fc4f1406f802c3a382858b08699
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluebreakpoint-interface1"></a><span data-ttu-id="61e05-102">ICorDebugValueBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="61e05-102">ICorDebugValueBreakpoint Interface1</span></span>
<span data-ttu-id="61e05-103">Rozszerzenie interfejsu ICorDebugBreakpoint w celu zapewnienia dostępu do określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="61e05-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61e05-104">Metody</span><span class="sxs-lookup"><span data-stu-id="61e05-104">Methods</span></span>  
  
|<span data-ttu-id="61e05-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="61e05-105">Method</span></span>|<span data-ttu-id="61e05-106">Opis</span><span class="sxs-lookup"><span data-stu-id="61e05-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61e05-107">GetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="61e05-107">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="61e05-108">Pobiera wskaźnika interfejsu do obiektu ICorDebugValue reprezentujący wartość obiektu, na którym jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="61e05-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61e05-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61e05-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61e05-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="61e05-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e05-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61e05-111">Requirements</span></span>  
 <span data-ttu-id="61e05-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61e05-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61e05-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61e05-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61e05-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61e05-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61e05-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61e05-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e05-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61e05-116">See Also</span></span>  
 [<span data-ttu-id="61e05-117">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="61e05-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
