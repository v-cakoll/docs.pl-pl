---
title: ICorDebugAssembly, interfejs1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a6776467eb9f5eaaacadb2908de17fc277e495b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569183"
---
# <a name="icordebugassembly-interface1"></a><span data-ttu-id="2377f-102">ICorDebugAssembly, interfejs1</span><span class="sxs-lookup"><span data-stu-id="2377f-102">ICorDebugAssembly Interface1</span></span>
<span data-ttu-id="2377f-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="2377f-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2377f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2377f-104">Methods</span></span>  
  
|<span data-ttu-id="2377f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-105">Method</span></span>|<span data-ttu-id="2377f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2377f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2377f-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="2377f-108">Pobiera moduł wyliczający dla modułów są zawarte w zestawie.</span><span class="sxs-lookup"><span data-stu-id="2377f-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="2377f-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="2377f-110">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2377f-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="2377f-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="2377f-112">Nie jest zaimplementowany w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2377f-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="2377f-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="2377f-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="2377f-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="2377f-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="2377f-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="2377f-116">Pobiera wystąpienie ICorDebugProcess, w którym uruchomiony jest zestaw.</span><span class="sxs-lookup"><span data-stu-id="2377f-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2377f-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2377f-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2377f-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="2377f-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2377f-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2377f-119">Requirements</span></span>  
 <span data-ttu-id="2377f-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2377f-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2377f-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2377f-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2377f-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2377f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2377f-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2377f-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2377f-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2377f-124">See also</span></span>
- [<span data-ttu-id="2377f-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2377f-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
