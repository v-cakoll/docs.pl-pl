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
ms.openlocfilehash: dd31bf458dde043a04e24251cedcac585fd385f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793044"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="2c01b-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2c01b-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="2c01b-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="2c01b-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c01b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2c01b-104">Methods</span></span>  
  
|<span data-ttu-id="2c01b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2c01b-105">Method</span></span>|<span data-ttu-id="2c01b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2c01b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c01b-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="2c01b-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="2c01b-108">Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="2c01b-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c01b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c01b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c01b-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2c01b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c01b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c01b-111">Requirements</span></span>  
 <span data-ttu-id="2c01b-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c01b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c01b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2c01b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c01b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c01b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c01b-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c01b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c01b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c01b-116">See also</span></span>

- [<span data-ttu-id="2c01b-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2c01b-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2c01b-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2c01b-118">Debugging</span></span>](index.md)
