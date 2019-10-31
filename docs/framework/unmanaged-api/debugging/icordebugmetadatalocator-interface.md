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
ms.openlocfilehash: 1116945ae1a886f1b9491e0baf183e20c4fff177
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136617"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="6d98f-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6d98f-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="6d98f-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="6d98f-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d98f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6d98f-104">Methods</span></span>  
  
|<span data-ttu-id="6d98f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6d98f-105">Method</span></span>|<span data-ttu-id="6d98f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6d98f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6d98f-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="6d98f-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="6d98f-108">Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="6d98f-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d98f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d98f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d98f-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="6d98f-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d98f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d98f-111">Requirements</span></span>  
 <span data-ttu-id="6d98f-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d98f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d98f-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d98f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d98f-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d98f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d98f-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d98f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d98f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d98f-116">See also</span></span>

- [<span data-ttu-id="6d98f-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d98f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6d98f-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6d98f-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
