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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5509dd07bbb6c812a7ea2797c46002aaa161c46
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64619967"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="2af7d-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2af7d-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="2af7d-103">Służy jako abstrakcyjny interfejs podstawowy dla wyliczenia, które są używane w publikowanie informacji o procesach i domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2af7d-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2af7d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2af7d-104">Methods</span></span>  
  
|<span data-ttu-id="2af7d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2af7d-105">Method</span></span>|<span data-ttu-id="2af7d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2af7d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2af7d-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="2af7d-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="2af7d-108">Tworzy kopię `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2af7d-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="2af7d-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="2af7d-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="2af7d-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="2af7d-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="2af7d-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="2af7d-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="2af7d-112">Przenosi kursora na początku tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="2af7d-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="2af7d-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="2af7d-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="2af7d-114">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="2af7d-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2af7d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2af7d-115">Remarks</span></span>  
 <span data-ttu-id="2af7d-116">Następujące moduły wyliczające pochodzić od `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="2af7d-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="2af7d-117">Icorpublishappdomainenum —</span><span class="sxs-lookup"><span data-stu-id="2af7d-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="2af7d-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="2af7d-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="2af7d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2af7d-119">Requirements</span></span>  
 <span data-ttu-id="2af7d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af7d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af7d-121">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2af7d-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2af7d-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af7d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af7d-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af7d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af7d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2af7d-124">See also</span></span>

- [<span data-ttu-id="2af7d-125">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="2af7d-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="2af7d-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2af7d-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
