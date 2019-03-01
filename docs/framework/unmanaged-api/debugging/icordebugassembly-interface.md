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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2b802845e36e818a962484c1fea09cbcc1ceefd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974578"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="52c81-102">ICorDebugAssembly — Interfejs</span><span class="sxs-lookup"><span data-stu-id="52c81-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="52c81-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="52c81-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52c81-104">Metody</span><span class="sxs-lookup"><span data-stu-id="52c81-104">Methods</span></span>  
  
|<span data-ttu-id="52c81-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-105">Method</span></span>|<span data-ttu-id="52c81-106">Opis</span><span class="sxs-lookup"><span data-stu-id="52c81-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52c81-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="52c81-108">Pobiera moduł wyliczający dla modułów są zawarte w zestawie.</span><span class="sxs-lookup"><span data-stu-id="52c81-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="52c81-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="52c81-110">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="52c81-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="52c81-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="52c81-112">Nie jest zaimplementowany w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52c81-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="52c81-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="52c81-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="52c81-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="52c81-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="52c81-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="52c81-116">Pobiera wystąpienie ICorDebugProcess, w którym uruchomiony jest zestaw.</span><span class="sxs-lookup"><span data-stu-id="52c81-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52c81-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52c81-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52c81-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="52c81-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52c81-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52c81-119">Requirements</span></span>  
 <span data-ttu-id="52c81-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52c81-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52c81-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52c81-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52c81-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52c81-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52c81-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52c81-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52c81-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52c81-124">See also</span></span>
- [<span data-ttu-id="52c81-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="52c81-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
