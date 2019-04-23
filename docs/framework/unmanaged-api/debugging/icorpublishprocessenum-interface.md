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
ms.openlocfilehash: 5186df61eb82b29fcfa9776408498b748068e122
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173657"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="d73e0-102">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d73e0-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="d73e0-103">Podklasa klasy [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interfejs, który udostępnia metody umożliwiające przemierzają kolekcję [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) obiektów.</span><span class="sxs-lookup"><span data-stu-id="d73e0-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d73e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d73e0-104">Methods</span></span>  
  
|<span data-ttu-id="d73e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d73e0-105">Method</span></span>|<span data-ttu-id="d73e0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d73e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d73e0-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="d73e0-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="d73e0-108">Pobiera określoną liczbę `ICorPublishProcess` wystąpień z kolekcji, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="d73e0-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d73e0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d73e0-109">Remarks</span></span>  
 <span data-ttu-id="d73e0-110">`ICorPublishProcessEnum` Interfejsu implementuje metody abstrakcyjny interfejs [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="d73e0-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="d73e0-111">`ICorPublishProcessEnum` Tworzone jest wystąpienie przez [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d73e0-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="d73e0-112">Przejście przez kolekcję `ICorPublishProcess` obiektów opiera się na kryteria filtrowania, biorąc pod uwagę w czasie `ICorPublishProcessEnum` wystąpienie zostało utworzone.</span><span class="sxs-lookup"><span data-stu-id="d73e0-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73e0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d73e0-113">Requirements</span></span>  
 <span data-ttu-id="d73e0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d73e0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73e0-115">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d73e0-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d73e0-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d73e0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d73e0-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73e0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73e0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d73e0-118">See also</span></span>

- [<span data-ttu-id="d73e0-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d73e0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d73e0-120">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="d73e0-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
