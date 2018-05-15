---
title: ICorPublishProcessEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcessEnum
helpviewer_keywords:
- ICorPublishProcessEnum interface [.NET Framework debugging]
ms.assetid: aac8fcf9-ac09-437c-bd5c-2fda14ae1007
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd71a2bd4a52da8fa77592363e2eb7c8f5101fd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="72771-102">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="72771-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="72771-103">Podklasa [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interfejs, który udostępnia metody przechodzenia przez kolekcję [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="72771-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72771-104">Metody</span><span class="sxs-lookup"><span data-stu-id="72771-104">Methods</span></span>  
  
|<span data-ttu-id="72771-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="72771-105">Method</span></span>|<span data-ttu-id="72771-106">Opis</span><span class="sxs-lookup"><span data-stu-id="72771-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72771-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="72771-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="72771-108">Pobiera określoną liczbę `ICorPublishProcess` wystąpień z kolekcji, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="72771-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72771-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72771-109">Remarks</span></span>  
 <span data-ttu-id="72771-110">`ICorPublishProcessEnum` Interfejsu implementuje metody abstrakcyjnej interfejsu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="72771-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="72771-111">`ICorPublishProcessEnum` Wystąpienia jest tworzony przez [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="72771-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="72771-112">Przechodzenie kolekcji `ICorPublishProcess` obiektów jest oparta na kryteria filtrowania podane w tym czasie `ICorPublishProcessEnum` wystąpienie zostało utworzone.</span><span class="sxs-lookup"><span data-stu-id="72771-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72771-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72771-113">Requirements</span></span>  
 <span data-ttu-id="72771-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72771-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72771-115">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="72771-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="72771-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72771-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72771-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72771-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72771-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72771-118">See Also</span></span>  
 [<span data-ttu-id="72771-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="72771-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="72771-120">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="72771-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
