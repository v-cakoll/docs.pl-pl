---
title: ICorDebugMetaDataLocator — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1673b6045a6344ee0eeadf4ec3003206f92cde4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="4e846-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4e846-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="4e846-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="4e846-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e846-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4e846-104">Methods</span></span>  
  
|<span data-ttu-id="4e846-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4e846-105">Method</span></span>|<span data-ttu-id="4e846-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4e846-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e846-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="4e846-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="4e846-108">Pyta debugera do zwrócenia pełną ścieżkę do modułu, którego metadanych wymaganego do ukończenia operacji żądanej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="4e846-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e846-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e846-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e846-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="4e846-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e846-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e846-111">Requirements</span></span>  
 <span data-ttu-id="4e846-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e846-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e846-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e846-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e846-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e846-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e846-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e846-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e846-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e846-116">See Also</span></span>  
 [<span data-ttu-id="4e846-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4e846-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4e846-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4e846-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
