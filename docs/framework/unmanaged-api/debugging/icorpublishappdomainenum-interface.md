---
title: ICorPublishAppDomainEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum
helpviewer_keywords:
- ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f6d4af7c01f91dff77d6ba715ef845f523c7fb6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993554"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="faa2a-102">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="faa2a-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="faa2a-103">Podklasa klasy [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interfejs, który udostępnia metody umożliwiające przemierzają kolekcję [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiekty, które obecnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="faa2a-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="faa2a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="faa2a-104">Methods</span></span>  
  
|<span data-ttu-id="faa2a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="faa2a-105">Method</span></span>|<span data-ttu-id="faa2a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="faa2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="faa2a-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="faa2a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="faa2a-108">Pobiera określoną liczbę `ICorPublishAppDomain` wystąpień z kolekcji, począwszy od bieżącej pozycji.</span><span class="sxs-lookup"><span data-stu-id="faa2a-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="faa2a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faa2a-109">Remarks</span></span>  
 <span data-ttu-id="faa2a-110">`ICorPublishAppDomainEnum` Interfejsu implementuje metody abstrakcyjny interfejs [icorpublishenum —](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="faa2a-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa2a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="faa2a-111">Requirements</span></span>  
 <span data-ttu-id="faa2a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa2a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa2a-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="faa2a-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="faa2a-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="faa2a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="faa2a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa2a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faa2a-116">See also</span></span>

- [<span data-ttu-id="faa2a-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="faa2a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="faa2a-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="faa2a-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
