---
title: ICorDebugAssembly — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly
helpviewer_keywords:
- ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type:
- apiref
ms.openlocfilehash: dea3231e3bbb361b56254756c6d99b115f73e792
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133969"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="b2b2d-102">ICorDebugAssembly — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b2b2d-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="b2b2d-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2b2d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b2b2d-104">Methods</span></span>  
  
|<span data-ttu-id="b2b2d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-105">Method</span></span>|<span data-ttu-id="b2b2d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b2b2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2b2d-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="b2b2d-108">Pobiera moduł wyliczający dla modułów zawartych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="b2b2d-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="b2b2d-110">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to wystąpienie `ICorDebugAssembly`.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="b2b2d-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="b2b2d-112">Nie zaimplementowane w bieżącej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="b2b2d-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="b2b2d-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="b2b2d-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="b2b2d-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="b2b2d-116">Pobiera wystąpienie ICorDebugProcess, w którym jest uruchomiony zestaw.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2b2d-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2b2d-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2b2d-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b2b2d-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b2d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2b2d-119">Requirements</span></span>  
 <span data-ttu-id="b2b2d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b2d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b2d-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2b2d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2b2d-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b2b2d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2b2d-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b2d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b2d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2b2d-124">See also</span></span>

- [<span data-ttu-id="b2b2d-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b2b2d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
