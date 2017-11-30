---
title: "ICorPublish — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublish
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublish
helpviewer_keywords: ICorPublish interface [.NET Framework debugging]
ms.assetid: 87c4fcb2-7703-4a2e-afb6-42973381b960
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8eb3bd2da9529a681f7f3a09ef7eb78c776cc302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublish-interface"></a><span data-ttu-id="29abe-102">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="29abe-102">ICorPublish Interface</span></span>
<span data-ttu-id="29abe-103">Służy jako ogólne interfejs do publikowania informacji na temat procesów i informacji o domenach aplikacji w tych procesów.</span><span class="sxs-lookup"><span data-stu-id="29abe-103">Serves as the general interface for publishing information about processes and information about the application domains in those processes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29abe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29abe-104">Methods</span></span>  
  
|<span data-ttu-id="29abe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29abe-105">Method</span></span>|<span data-ttu-id="29abe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="29abe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29abe-107">EnumProcesses — metoda</span><span class="sxs-lookup"><span data-stu-id="29abe-107">EnumProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md)|<span data-ttu-id="29abe-108">Pobiera [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) wystąpienia, które zawiera zarządzanych procesów uruchomionych na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="29abe-108">Gets an [ICorPublishProcessEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md) instance that contains the managed processes running on this computer.</span></span>|  
|[<span data-ttu-id="29abe-109">GetProcess — metoda</span><span class="sxs-lookup"><span data-stu-id="29abe-109">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-getprocess-method.md)|<span data-ttu-id="29abe-110">Pobiera [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wystąpienia, który reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="29abe-110">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29abe-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29abe-111">Requirements</span></span>  
 <span data-ttu-id="29abe-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29abe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29abe-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="29abe-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29abe-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29abe-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29abe-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29abe-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29abe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29abe-116">See Also</span></span>  
 [<span data-ttu-id="29abe-117">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="29abe-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="29abe-118">Corpubpublish — klasa Coclass</span><span class="sxs-lookup"><span data-stu-id="29abe-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
