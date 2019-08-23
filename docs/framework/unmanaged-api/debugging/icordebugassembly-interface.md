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
ms.openlocfilehash: 426269d14992ae0f1f8c02619b259cfdd4bcbf8f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959440"
---
# <a name="icordebugassembly-interface"></a><span data-ttu-id="821fe-102">ICorDebugAssembly, interfejs</span><span class="sxs-lookup"><span data-stu-id="821fe-102">ICorDebugAssembly Interface</span></span>

<span data-ttu-id="821fe-103">Reprezentuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="821fe-103">Represents an assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="821fe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="821fe-104">Methods</span></span>  
  
|<span data-ttu-id="821fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-105">Method</span></span>|<span data-ttu-id="821fe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="821fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="821fe-107">EnumerateModules, metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-107">EnumerateModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md)|<span data-ttu-id="821fe-108">Pobiera moduł wyliczający dla modułów zawartych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="821fe-108">Gets an enumerator for the modules contained in the assembly.</span></span>|  
|[<span data-ttu-id="821fe-109">GetAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-109">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getappdomain-method.md)|<span data-ttu-id="821fe-110">Pobiera wskaźnik interfejsu do domeny aplikacji, która zawiera to `ICorDebugAssembly` wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="821fe-110">Gets an interface pointer to the application domain that contains this `ICorDebugAssembly` instance.</span></span>|  
|[<span data-ttu-id="821fe-111">GetCodeBase, metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-111">GetCodeBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getcodebase-method.md)|<span data-ttu-id="821fe-112">Nie zaimplementowane w bieżącej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="821fe-112">Not implemented in the current version of the .NET Framework.</span></span>|  
|[<span data-ttu-id="821fe-113">GetName, metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getname-method.md)|<span data-ttu-id="821fe-114">Pobiera nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="821fe-114">Gets the name of the assembly.</span></span>|  
|[<span data-ttu-id="821fe-115">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="821fe-115">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-getprocess-method.md)|<span data-ttu-id="821fe-116">Pobiera wystąpienie ICorDebugProcess, w którym jest uruchomiony zestaw.</span><span class="sxs-lookup"><span data-stu-id="821fe-116">Gets the ICorDebugProcess instance in which the assembly is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="821fe-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="821fe-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="821fe-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="821fe-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="821fe-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="821fe-119">Requirements</span></span>  
 <span data-ttu-id="821fe-120">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="821fe-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="821fe-121">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="821fe-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="821fe-122">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="821fe-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="821fe-123">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="821fe-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821fe-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="821fe-124">See also</span></span>

- [<span data-ttu-id="821fe-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="821fe-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
