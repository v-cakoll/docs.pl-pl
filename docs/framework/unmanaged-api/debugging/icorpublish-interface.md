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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1dea8cc54c68db333c409e3bd7b3e4211bd52ac
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713970"
---
# <a name="icorpublish-interface"></a><span data-ttu-id="1ef8c-102">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1ef8c-102">ICorPublish Interface</span></span>
<span data-ttu-id="1ef8c-103">Służy jako ogólny interfejs do publikowania informacji na temat procesów i informacji na temat domen aplikacji w tych procesów.</span><span class="sxs-lookup"><span data-stu-id="1ef8c-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1ef8c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1ef8c-104">Methods</span></span>  
  
|<span data-ttu-id="1ef8c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1ef8c-105">Method</span></span>|<span data-ttu-id="1ef8c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1ef8c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1ef8c-107">EnumProcesses, metoda</span><span class="sxs-lookup"><span data-stu-id="1ef8c-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="1ef8c-108">Pobiera [icorpublishprocessenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienia, które zawiera zarządzane procesy uruchomione na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1ef8c-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="1ef8c-109">GetProcess, metoda</span><span class="sxs-lookup"><span data-stu-id="1ef8c-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="1ef8c-110">Pobiera [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wystąpienia, który reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="1ef8c-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1ef8c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ef8c-111">Requirements</span></span>  
 <span data-ttu-id="1ef8c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ef8c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ef8c-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="1ef8c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1ef8c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ef8c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ef8c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ef8c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ef8c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ef8c-116">See also</span></span>
- [<span data-ttu-id="1ef8c-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1ef8c-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="1ef8c-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="1ef8c-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
