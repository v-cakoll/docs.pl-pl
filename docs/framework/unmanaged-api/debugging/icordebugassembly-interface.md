---
title: ICorDebugAssembly, interfejs
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
ms.openlocfilehash: 3dd60defc1c003fa4b235ddcb0a78b9a819b1b0c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198026"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="152c9-102">ICorDebugAssembly, interfejs</span><span class="sxs-lookup"><span data-stu-id="152c9-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="152c9-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="152c9-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="152c9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="152c9-104">Methods</span></span>  
  
|<span data-ttu-id="152c9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-105">Method</span></span>|<span data-ttu-id="152c9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="152c9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="152c9-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="152c9-108">Pobiera moduł wyliczający dla modułów są zawarte w zestawie.</span><span class="sxs-lookup"><span data-stu-id="152c9-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="152c9-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="152c9-110">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="152c9-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="152c9-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="152c9-112">Nie jest zaimplementowany w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="152c9-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="152c9-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="152c9-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="152c9-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="152c9-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="152c9-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="152c9-116">Pobiera wystąpienie ICorDebugProcess, w którym uruchomiony jest zestaw.</span><span class="sxs-lookup"><span data-stu-id="152c9-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="152c9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="152c9-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="152c9-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="152c9-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152c9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="152c9-119">Requirements</span></span>  
 <span data-ttu-id="152c9-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="152c9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152c9-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="152c9-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="152c9-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="152c9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="152c9-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152c9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="152c9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="152c9-124">See also</span></span>

- [<span data-ttu-id="152c9-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="152c9-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
