---
title: ICorDebugHandleValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6ba8a738b4086b9150e0a1c7b300a519fa3092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419110"
---
# <a name="icordebughandlevalue-interface1"></a><span data-ttu-id="fc11e-102">ICorDebugHandleValue Interface1</span><span class="sxs-lookup"><span data-stu-id="fc11e-102">ICorDebugHandleValue Interface1</span></span>
<span data-ttu-id="fc11e-103">Podklasa ICorDebugReferenceValue reprezentujący wartość odwołania, do których debuger został utworzony obsługę wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="fc11e-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc11e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fc11e-104">Methods</span></span>  
  
|<span data-ttu-id="fc11e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc11e-105">Method</span></span>|<span data-ttu-id="fc11e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fc11e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc11e-107">Dispose, metoda</span><span class="sxs-lookup"><span data-stu-id="fc11e-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="fc11e-108">Zwalnia odwołuje się ta dojścia `ICorDebugHandleValue` obiektu bez jawnego zwolnienia wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fc11e-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="fc11e-109">GetHandleType, metoda</span><span class="sxs-lookup"><span data-stu-id="fc11e-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="fc11e-110">Pobiera wartość CorDebugHandleType, która opisuje rodzaj odwołuje się ta dojścia `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="fc11e-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc11e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc11e-111">Remarks</span></span>  
 <span data-ttu-id="fc11e-112">`ICorDebugReferenceValue` Obiektu jest unieważnienie podziału wykonywania debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="fc11e-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="fc11e-113">`ICorDebugHandleValue` Przechowuje odwołanie do podziału i kontynuacje, do momentu jego jawnego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="fc11e-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc11e-114">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="fc11e-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc11e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc11e-115">Requirements</span></span>  
 <span data-ttu-id="fc11e-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc11e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc11e-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc11e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc11e-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc11e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc11e-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc11e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc11e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc11e-120">See Also</span></span>  
 [<span data-ttu-id="fc11e-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fc11e-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
