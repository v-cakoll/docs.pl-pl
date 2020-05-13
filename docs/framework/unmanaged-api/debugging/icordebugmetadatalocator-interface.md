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
ms.openlocfilehash: 7b7b7a42edea775d1aaa850ccfc532ef86749991
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210028"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="ad7c0-102">ICorDebugMetaDataLocator — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ad7c0-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="ad7c0-103">Dostarcza informacje o metadanych do debugera.</span><span class="sxs-lookup"><span data-stu-id="ad7c0-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ad7c0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ad7c0-104">Methods</span></span>  
  
|<span data-ttu-id="ad7c0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ad7c0-105">Method</span></span>|<span data-ttu-id="ad7c0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ad7c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ad7c0-107">GetMetaData, metoda</span><span class="sxs-lookup"><span data-stu-id="ad7c0-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="ad7c0-108">Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.</span><span class="sxs-lookup"><span data-stu-id="ad7c0-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad7c0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad7c0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad7c0-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="ad7c0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad7c0-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad7c0-111">Requirements</span></span>  
 <span data-ttu-id="ad7c0-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad7c0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad7c0-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ad7c0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad7c0-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ad7c0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad7c0-115">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad7c0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7c0-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad7c0-116">See also</span></span>

- [<span data-ttu-id="ad7c0-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ad7c0-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ad7c0-118">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ad7c0-118">Debugging</span></span>](index.md)
