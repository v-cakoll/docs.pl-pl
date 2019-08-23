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
ms.openlocfilehash: 64cf11ec294486fdc14d424e731eac8e4745d892
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939863"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="8b32e-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8b32e-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="8b32e-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="8b32e-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b32e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b32e-104">Methods</span></span>  
  
|<span data-ttu-id="8b32e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b32e-105">Method</span></span>|<span data-ttu-id="8b32e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8b32e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b32e-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="8b32e-107">GetMetaData Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="8b32e-108">Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="8b32e-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b32e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b32e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b32e-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="8b32e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b32e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b32e-111">Requirements</span></span>  
 <span data-ttu-id="8b32e-112">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b32e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b32e-113">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b32e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b32e-114">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b32e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b32e-115">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b32e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b32e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b32e-116">See also</span></span>

- [<span data-ttu-id="8b32e-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8b32e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8b32e-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8b32e-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
