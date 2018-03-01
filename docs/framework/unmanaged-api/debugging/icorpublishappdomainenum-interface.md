---
title: "ICorPublishAppDomainEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3f84a93053744f059eb3fdd06e2fb69e098e24ef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="8ad6d-102">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8ad6d-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="8ad6d-103">Podklasa [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interfejs, który udostępnia metody przechodzenia przez kolekcję [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) obiekty znajdujące się obecnie w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="8ad6d-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8ad6d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8ad6d-104">Methods</span></span>  
  
|<span data-ttu-id="8ad6d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8ad6d-105">Method</span></span>|<span data-ttu-id="8ad6d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8ad6d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8ad6d-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="8ad6d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="8ad6d-108">Pobiera określoną liczbę `ICorPublishAppDomain` wystąpień z kolekcji, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="8ad6d-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ad6d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ad6d-109">Remarks</span></span>  
 <span data-ttu-id="8ad6d-110">`ICorPublishAppDomainEnum` Interfejsu implementuje metody abstrakcyjnej interfejsu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6d-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad6d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ad6d-111">Requirements</span></span>  
 <span data-ttu-id="8ad6d-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad6d-113">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="8ad6d-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8ad6d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ad6d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ad6d-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad6d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad6d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ad6d-116">See Also</span></span>  
 [<span data-ttu-id="8ad6d-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8ad6d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8ad6d-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="8ad6d-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
