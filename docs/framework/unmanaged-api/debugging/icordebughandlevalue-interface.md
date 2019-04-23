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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59117446"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="95721-102">ICorDebugHandleValue, interfejs</span><span class="sxs-lookup"><span data-stu-id="95721-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="95721-103">Podklasa klasy ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="95721-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="95721-104">Metody</span><span class="sxs-lookup"><span data-stu-id="95721-104">Methods</span></span>  
  
|<span data-ttu-id="95721-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="95721-105">Method</span></span>|<span data-ttu-id="95721-106">Opis</span><span class="sxs-lookup"><span data-stu-id="95721-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="95721-107">Dispose, metoda</span><span class="sxs-lookup"><span data-stu-id="95721-107">Dispose Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|<span data-ttu-id="95721-108">Zwalnia dojście przywoływane przez to `ICorDebugHandleValue` obiektu bez jawnie zwalniania wskaźnika interfejsu.</span><span class="sxs-lookup"><span data-stu-id="95721-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="95721-109">GetHandleType, metoda</span><span class="sxs-lookup"><span data-stu-id="95721-109">GetHandleType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="95721-110">Pobiera wartość cordebughandletype —, która opisuje typ dojścia przywoływane przez to `ICorDebugHandleValue`.</span><span class="sxs-lookup"><span data-stu-id="95721-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95721-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95721-111">Remarks</span></span>  
 <span data-ttu-id="95721-112">`ICorDebugReferenceValue` Obiektu zostaje unieważniony przez przerwy podczas wykonywania debugowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="95721-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="95721-113">`ICorDebugHandleValue` Przechowuje swoje odwołanie do podziału i kontynuacji, do jego jawnego zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="95721-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95721-114">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="95721-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95721-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95721-115">Requirements</span></span>  
 <span data-ttu-id="95721-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95721-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95721-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95721-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95721-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95721-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95721-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95721-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95721-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95721-120">See also</span></span>

- [<span data-ttu-id="95721-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="95721-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
