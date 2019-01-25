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
ms.openlocfilehash: c1ee52e993859963984f7468e41a5daf3a77ba26
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621675"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="edd80-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="edd80-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="edd80-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="edd80-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="edd80-104">Metody</span><span class="sxs-lookup"><span data-stu-id="edd80-104">Methods</span></span>  
  
|<span data-ttu-id="edd80-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="edd80-105">Method</span></span>|<span data-ttu-id="edd80-106">Opis</span><span class="sxs-lookup"><span data-stu-id="edd80-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="edd80-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="edd80-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="edd80-108">Pyta, czy debugera, aby przywrócić pełną ścieżkę do modułu, którego metadanych jest potrzebne do ukończenia operacja, którą żądany debuger.</span><span class="sxs-lookup"><span data-stu-id="edd80-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edd80-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edd80-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="edd80-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="edd80-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edd80-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edd80-111">Requirements</span></span>  
 <span data-ttu-id="edd80-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edd80-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edd80-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edd80-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edd80-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edd80-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edd80-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edd80-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd80-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edd80-116">See also</span></span>
- [<span data-ttu-id="edd80-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="edd80-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="edd80-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="edd80-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
