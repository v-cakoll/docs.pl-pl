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
ms.openlocfilehash: 61cac0922423acabef3d47618d98ddf082d071da
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790675"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="06518-102">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="06518-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="06518-103">Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="06518-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="06518-104">Metody</span><span class="sxs-lookup"><span data-stu-id="06518-104">Methods</span></span>  
  
|<span data-ttu-id="06518-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="06518-105">Method</span></span>|<span data-ttu-id="06518-106">Opis</span><span class="sxs-lookup"><span data-stu-id="06518-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="06518-107">Next, metoda</span><span class="sxs-lookup"><span data-stu-id="06518-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="06518-108">Pobiera określoną liczbę wystąpień `ICorPublishAppDomain` z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="06518-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06518-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06518-109">Remarks</span></span>  
 <span data-ttu-id="06518-110">Interfejs `ICorPublishAppDomainEnum` implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="06518-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06518-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06518-111">Requirements</span></span>  
 <span data-ttu-id="06518-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06518-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06518-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="06518-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="06518-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="06518-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06518-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06518-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06518-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06518-116">See also</span></span>

- [<span data-ttu-id="06518-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="06518-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="06518-118">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="06518-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
