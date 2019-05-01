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
ms.openlocfilehash: 1eac0b9fe252e476f8ff781f2181a203886d3beb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993541"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="01595-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="01595-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="01595-103">Służy jako abstrakcyjny interfejs podstawowy dla wyliczenia, które są używane w publikowanie informacji o procesach i domen aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01595-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="01595-104">Metody</span><span class="sxs-lookup"><span data-stu-id="01595-104">Methods</span></span>  
  
|<span data-ttu-id="01595-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="01595-105">Method</span></span>|<span data-ttu-id="01595-106">Opis</span><span class="sxs-lookup"><span data-stu-id="01595-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="01595-107">Clone, metoda</span><span class="sxs-lookup"><span data-stu-id="01595-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-clone-method.md)|<span data-ttu-id="01595-108">Tworzy kopię `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="01595-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="01595-109">GetCount, metoda</span><span class="sxs-lookup"><span data-stu-id="01595-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-getcount-method.md)|<span data-ttu-id="01595-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="01595-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="01595-111">Reset, metoda</span><span class="sxs-lookup"><span data-stu-id="01595-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-reset-method.md)|<span data-ttu-id="01595-112">Przenosi kursora na początku tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="01595-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="01595-113">Skip, metoda</span><span class="sxs-lookup"><span data-stu-id="01595-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-skip-method.md)|<span data-ttu-id="01595-114">Przesuwa kursor do przodu w wyliczeniu przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="01595-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01595-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01595-115">Remarks</span></span>  
 <span data-ttu-id="01595-116">Następujące moduły wyliczające pochodzić od `ICorPublishEnum`:</span><span class="sxs-lookup"><span data-stu-id="01595-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="01595-117">Icorpublishappdomainenum —</span><span class="sxs-lookup"><span data-stu-id="01595-117">ICorPublishAppDomainEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="01595-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="01595-118">ICorPublishProcessEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="01595-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01595-119">Requirements</span></span>  
 <span data-ttu-id="01595-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01595-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01595-121">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="01595-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="01595-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01595-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01595-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01595-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01595-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01595-124">See also</span></span>

- [<span data-ttu-id="01595-125">CorpubPublish, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="01595-125">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)
- [<span data-ttu-id="01595-126">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01595-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
