---
title: ICorDebugModule2, interfejs1
ms.date: 03/30/2017
api_name:
- ICorDebugModule2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2
helpviewer_keywords:
- ICorDebugModule2 interface [.NET Framework debugging]
ms.assetid: 0847e64f-fdbe-4c96-8168-da20fdc84d80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c65d2da485664691ff71044eb4e44f12108ce5b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707599"
---
# <a name="icordebugmodule2-interface1"></a><span data-ttu-id="0c789-102">ICorDebugModule2, interfejs1</span><span class="sxs-lookup"><span data-stu-id="0c789-102">ICorDebugModule2 Interface1</span></span>
<span data-ttu-id="0c789-103">Służy jako logiczne rozszerzenie icordebugmodule — interfejs.</span><span class="sxs-lookup"><span data-stu-id="0c789-103">Serves as a logical extension to the ICorDebugModule interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c789-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0c789-104">Methods</span></span>  
  
|<span data-ttu-id="0c789-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-105">Method</span></span>|<span data-ttu-id="0c789-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0c789-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c789-107">ApplyChanges, metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-107">ApplyChanges Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-applychanges-method.md)|<span data-ttu-id="0c789-108">Ma zastosowanie zmian w metadanych i zmiany w kodzie języka intermediate language (MSIL) firmy Microsoft do uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="0c789-108">Applies the changes in the metadata and the changes in the Microsoft intermediate language (MSIL) code to the running process.</span></span>|  
|[<span data-ttu-id="0c789-109">GetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-109">GetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-getjitcompilerflags-method.md)|<span data-ttu-id="0c789-110">Pobiera flagi, które kontrolują kompilację just-in-time (JIT), w tym `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="0c789-110">Gets the flags that control the just-in-time (JIT) compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="0c789-111">ResolveAssembly, metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-111">ResolveAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-resolveassembly-method.md)|<span data-ttu-id="0c789-112">Usuwa zestaw odwołuje się token określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="0c789-112">Resolves the assembly referenced by the specified metadata token.</span></span>|  
|[<span data-ttu-id="0c789-113">SetJITCompilerFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-113">SetJITCompilerFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjitcompilerflags-method.md)|<span data-ttu-id="0c789-114">Ustawia flagi, które kontrolują kompilację JIT dla tej `ICorDebugModule2`.</span><span class="sxs-lookup"><span data-stu-id="0c789-114">Sets the flags that control the JIT compilation for this `ICorDebugModule2`.</span></span>|  
|[<span data-ttu-id="0c789-115">SetJMCStatus, metoda</span><span class="sxs-lookup"><span data-stu-id="0c789-115">SetJMCStatus Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-setjmcstatus-method.md)|<span data-ttu-id="0c789-116">Ustawia stan tylko mój kod (JMC) wszystkich metod wszystkie klasy w tym `ICorDebugModule2` do określonej wartości, z wyjątkiem tych `pTokens` tablicy, która ustawia przeciwną wartość.</span><span class="sxs-lookup"><span data-stu-id="0c789-116">Sets the Just My Code (JMC) status of all methods of all the classes in this `ICorDebugModule2` to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c789-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c789-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c789-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="0c789-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c789-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c789-119">Requirements</span></span>  
 <span data-ttu-id="0c789-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c789-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c789-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c789-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c789-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c789-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c789-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c789-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c789-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c789-124">See also</span></span>
- [<span data-ttu-id="0c789-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c789-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
