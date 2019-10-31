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
ms.openlocfilehash: 3a7267548a957d403cfe02aa3d800a410c14b82a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103420"
---
# <a name="icorpublishprocessenum-interface"></a><span data-ttu-id="41a66-102">ICorPublishProcessEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="41a66-102">ICorPublishProcessEnum Interface</span></span>
<span data-ttu-id="41a66-103">Podklasa interfejsu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="41a66-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41a66-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41a66-104">Methods</span></span>  
  
|<span data-ttu-id="41a66-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41a66-105">Method</span></span>|<span data-ttu-id="41a66-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41a66-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41a66-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="41a66-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-next-method.md)|<span data-ttu-id="41a66-108">Pobiera określoną liczbę wystąpień `ICorPublishProcess` z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="41a66-108">Gets the specified number of `ICorPublishProcess` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41a66-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41a66-109">Remarks</span></span>  
 <span data-ttu-id="41a66-110">Interfejs `ICorPublishProcessEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="41a66-110">The `ICorPublishProcessEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
 <span data-ttu-id="41a66-111">Wystąpienie `ICorPublishProcessEnum` jest tworzone przez metodę [ICorPublish:: EnumProcesses —](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) .</span><span class="sxs-lookup"><span data-stu-id="41a66-111">An `ICorPublishProcessEnum` instance is created by the [ICorPublish::EnumProcesses](../../../../docs/framework/unmanaged-api/debugging/icorpublish-enumprocesses-method.md) method.</span></span> <span data-ttu-id="41a66-112">Przechodzenie kolekcji obiektów `ICorPublishProcess` jest oparte na kryteriach filtrowania określonych w momencie utworzenia wystąpienia `ICorPublishProcessEnum`.</span><span class="sxs-lookup"><span data-stu-id="41a66-112">The traversal of the collection of `ICorPublishProcess` objects is based on the filter criteria given at the time the `ICorPublishProcessEnum` instance was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41a66-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41a66-113">Requirements</span></span>  
 <span data-ttu-id="41a66-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41a66-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41a66-115">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="41a66-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="41a66-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41a66-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41a66-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41a66-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41a66-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41a66-118">See also</span></span>

- [<span data-ttu-id="41a66-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41a66-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="41a66-120">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="41a66-120">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
