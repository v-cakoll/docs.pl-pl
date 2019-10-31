---
title: ICorPublishEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorPublishEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum
helpviewer_keywords:
- ICorPublishEnum interface [.NET Framework debugging]
ms.assetid: 76a136b5-e444-417a-8ade-f1596d597dc7
topic_type:
- apiref
ms.openlocfilehash: 7d083655326333f18ee98f8e84fff2ed182dde6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103462"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="53f16-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="53f16-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="53f16-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane w publikowaniu informacji o procesach i domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="53f16-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53f16-104">Metody</span><span class="sxs-lookup"><span data-stu-id="53f16-104">Methods</span></span>  
  
|<span data-ttu-id="53f16-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="53f16-105">Method</span></span>|<span data-ttu-id="53f16-106">Opis</span><span class="sxs-lookup"><span data-stu-id="53f16-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53f16-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="53f16-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="53f16-108">Tworzy kopię tego obiektu `ICorPublishEnum`.</span><span class="sxs-lookup"><span data-stu-id="53f16-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="53f16-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="53f16-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="53f16-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="53f16-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="53f16-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="53f16-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="53f16-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="53f16-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="53f16-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="53f16-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="53f16-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="53f16-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53f16-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53f16-115">Remarks</span></span>  
 <span data-ttu-id="53f16-116">Następujące moduły wyliczające pochodzą z `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="53f16-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="53f16-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="53f16-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="53f16-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="53f16-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="53f16-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53f16-119">Requirements</span></span>  
 <span data-ttu-id="53f16-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53f16-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53f16-121">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="53f16-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="53f16-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="53f16-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53f16-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53f16-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f16-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53f16-124">See also</span></span>

- [<span data-ttu-id="53f16-125">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="53f16-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="53f16-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="53f16-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
