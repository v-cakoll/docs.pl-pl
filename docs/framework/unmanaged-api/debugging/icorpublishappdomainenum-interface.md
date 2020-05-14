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
ms.openlocfilehash: a48e20413f466e25a9145e9dbf1ba93d90155770
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397032"
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="725f6-102">ICorPublishAppDomainEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="725f6-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="725f6-103">Podklasa interfejsu [ICorPublishEnum](icorpublishenum-interface.md) , która dostarcza metody umożliwiające przechodzenie kolekcji obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , które aktualnie istnieją w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="725f6-103">A subclass of the [ICorPublishEnum](icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="725f6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="725f6-104">Methods</span></span>  
  
|<span data-ttu-id="725f6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="725f6-105">Method</span></span>|<span data-ttu-id="725f6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="725f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="725f6-107">Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="725f6-107">Next Method</span></span>](icorpublishappdomainenum-next-method.md)|<span data-ttu-id="725f6-108">Pobiera określoną liczbę `ICorPublishAppDomain` wystąpień z kolekcji, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="725f6-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="725f6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="725f6-109">Remarks</span></span>  
 <span data-ttu-id="725f6-110">`ICorPublishAppDomainEnum`Interfejs implementuje metody interfejsu abstrakcyjnego, [ICorPublishEnum](icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="725f6-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="725f6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="725f6-111">Requirements</span></span>  
 <span data-ttu-id="725f6-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="725f6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="725f6-113">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="725f6-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="725f6-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="725f6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="725f6-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="725f6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725f6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="725f6-116">See also</span></span>

- [<span data-ttu-id="725f6-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="725f6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="725f6-118">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="725f6-118">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
