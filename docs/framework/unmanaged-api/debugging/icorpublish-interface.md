---
title: ICorPublish — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublish
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish
helpviewer_keywords:
- ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type:
- apiref
ms.openlocfilehash: 70cf2d76c7c5d1c3431506685f8506e44ab9ec4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121765"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="ab233-102">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab233-102">ICorPublish Interface</span></span>
<span data-ttu-id="ab233-103">Służy jako ogólny interfejs publikowania informacji o procesach i informacjach o domenach aplikacji w tych procesach.</span><span class="sxs-lookup"><span data-stu-id="ab233-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab233-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab233-104">Methods</span></span>  
  
|<span data-ttu-id="ab233-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab233-105">Method</span></span>|<span data-ttu-id="ab233-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab233-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab233-107">EnumProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="ab233-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="ab233-108">Pobiera wystąpienie [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) , które zawiera zarządzane procesy uruchomione na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab233-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="ab233-109">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="ab233-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="ab233-110">Pobiera wystąpienie [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) , które reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="ab233-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab233-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab233-111">Requirements</span></span>  
 <span data-ttu-id="ab233-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab233-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab233-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ab233-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ab233-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ab233-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab233-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab233-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab233-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab233-116">See also</span></span>

- [<span data-ttu-id="ab233-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab233-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ab233-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="ab233-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
