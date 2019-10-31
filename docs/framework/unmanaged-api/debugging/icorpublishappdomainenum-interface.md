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
ms.openlocfilehash: cbe2aa48a8b67b0b6e88f7b5267bc70848fe3cec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140326"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="fad92-102">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fad92-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="fad92-103">Podklasa interfejsu [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) , które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="fad92-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fad92-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fad92-104">Methods</span></span>  
  
|<span data-ttu-id="fad92-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fad92-105">Method</span></span>|<span data-ttu-id="fad92-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fad92-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fad92-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="fad92-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="fad92-108">Pobiera określoną liczbę wystąpień `ICorPublishAppDomain` z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="fad92-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fad92-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fad92-109">Remarks</span></span>  
 <span data-ttu-id="fad92-110">Interfejs `ICorPublishAppDomainEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fad92-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fad92-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fad92-111">Requirements</span></span>  
 <span data-ttu-id="fad92-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fad92-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fad92-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="fad92-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fad92-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fad92-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fad92-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fad92-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fad92-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fad92-116">See also</span></span>

- [<span data-ttu-id="fad92-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fad92-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fad92-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="fad92-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
