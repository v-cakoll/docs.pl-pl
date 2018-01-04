---
title: "ICorPublishEnum — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum
helpviewer_keywords: ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f09d0f80eba86d03d0db7af8fd63d2231c9a88d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="b1223-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1223-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="b1223-103">Pełni rolę abstrakcyjnej interfejs podstawowy dla wyliczenia, które są używane w publikowaniu informacji o procesach i domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1223-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1223-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1223-104">Methods</span></span>  
  
|<span data-ttu-id="b1223-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1223-105">Method</span></span>|<span data-ttu-id="b1223-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b1223-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1223-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="b1223-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="b1223-108">Tworzy kopię tego `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="b1223-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="b1223-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="b1223-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="b1223-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="b1223-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b1223-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="b1223-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="b1223-112">Przesuwa kursor na początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b1223-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b1223-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="b1223-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="b1223-114">Przesuwa kursor do przodu w wyliczeniu określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="b1223-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1223-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1223-115">Remarks</span></span>  
 <span data-ttu-id="b1223-116">Następujące moduły wyliczające pochodzi od `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="b1223-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
-   [<span data-ttu-id="b1223-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b1223-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
-   [<span data-ttu-id="b1223-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b1223-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="b1223-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1223-119">Requirements</span></span>  
 <span data-ttu-id="b1223-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1223-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1223-121">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b1223-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b1223-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1223-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1223-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1223-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1223-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1223-124">See Also</span></span>  
 [<span data-ttu-id="b1223-125">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="b1223-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)  
 [<span data-ttu-id="b1223-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b1223-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
