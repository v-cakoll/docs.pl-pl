---
title: ICorDebugAssembly Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAssembly
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAssembly
helpviewer_keywords: ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: 9d657a28-6984-4c5e-8a54-89d20080baff
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6331c00c2be0805afb56028e9e1a13cd11168cf1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="fe10c-102">ICorDebugAssembly Interface1</span><span class="sxs-lookup"><span data-stu-id="fe10c-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="fe10c-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="fe10c-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe10c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fe10c-104">Methods</span></span>  
  
|<span data-ttu-id="fe10c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-105">Method</span></span>|<span data-ttu-id="fe10c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fe10c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe10c-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="fe10c-108">Pobiera moduł wyliczający dla modułów zawartych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="fe10c-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="fe10c-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="fe10c-110">Pobiera wskaźnika interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fe10c-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="fe10c-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="fe10c-112">Nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe10c-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="fe10c-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="fe10c-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="fe10c-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="fe10c-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="fe10c-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="fe10c-116">Pobiera wystąpienie ICorDebugProcess, w którym jest uruchomiony zestawu.</span><span class="sxs-lookup"><span data-stu-id="fe10c-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe10c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fe10c-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe10c-118">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="fe10c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe10c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe10c-119">Requirements</span></span>  
 <span data-ttu-id="fe10c-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe10c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe10c-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe10c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe10c-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe10c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe10c-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe10c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe10c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe10c-124">See Also</span></span>  
 [<span data-ttu-id="fe10c-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fe10c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
