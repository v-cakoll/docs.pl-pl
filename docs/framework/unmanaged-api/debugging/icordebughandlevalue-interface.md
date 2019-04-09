---
title: ICorDebugHandleValue, interfejs
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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117446"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="6579f-102">ICorDebugHandleValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="6579f-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="6579f-103">Podklasa klasy ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="6579f-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6579f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6579f-104">Methods</span></span>  
  
|<span data-ttu-id="6579f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6579f-105">Method</span></span>|<span data-ttu-id="6579f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6579f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6579f-107">Dispose — Metoda</span><span class="sxs-lookup"><span data-stu-id="6579f-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="6579f-108">Zwalnia dojście przywoływane przez to `ICorDebugHandleValue` obiektu bez jawnie zwalniania wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6579f-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="6579f-109">GetHandleType, metoda</span><span class="sxs-lookup"><span data-stu-id="6579f-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="6579f-110">Pobiera wartość cordebughandletype —, która opisuje typ dojścia przywoływane przez to `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="6579f-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6579f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6579f-111">Remarks</span></span>  
 <span data-ttu-id="6579f-112">`ICorDebugReferenceValue` Obiektu zostaje unieważniony przez przerwy podczas wykonywania debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="6579f-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="6579f-113">`ICorDebugHandleValue` Przechowuje swoje odwołanie do podziału i kontynuacji, do jego jawnego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="6579f-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6579f-114">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="6579f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6579f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6579f-115">Requirements</span></span>  
 <span data-ttu-id="6579f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6579f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6579f-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6579f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6579f-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6579f-118">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6579f-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6579f-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6579f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6579f-120">See also</span></span>

- [<span data-ttu-id="6579f-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6579f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
