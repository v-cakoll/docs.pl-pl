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
ms.openlocfilehash: acbc37d0f49af21c60ff6989932c5d341673512b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421179"
---
# <a name="icorpublishenum-interface"></a><span data-ttu-id="4e378-102">ICorPublishEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4e378-102">ICorPublishEnum Interface</span></span>
<span data-ttu-id="4e378-103">Służy jako abstrakcyjny interfejs podstawowy dla modułów wyliczających, które są używane w publikowaniu informacji o procesach i domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4e378-103">Serves as the abstract base interface for the enumerators that are used in the publishing of information about processes and application domains.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4e378-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4e378-104">Methods</span></span>  
  
|<span data-ttu-id="4e378-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4e378-105">Method</span></span>|<span data-ttu-id="4e378-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4e378-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4e378-107">Clone — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e378-107">Clone Method</span></span>](icorpublishenum-clone-method.md)|<span data-ttu-id="4e378-108">Tworzy kopię tego `ICorPublishEnum` obiektu.</span><span class="sxs-lookup"><span data-stu-id="4e378-108">Creates a copy of this `ICorPublishEnum` object.</span></span>|  
|[<span data-ttu-id="4e378-109">GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e378-109">GetCount Method</span></span>](icorpublishenum-getcount-method.md)|<span data-ttu-id="4e378-110">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="4e378-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="4e378-111">Reset — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e378-111">Reset Method</span></span>](icorpublishenum-reset-method.md)|<span data-ttu-id="4e378-112">Przenosi kursor do początku wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4e378-112">Moves the cursor of to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="4e378-113">Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="4e378-113">Skip Method</span></span>](icorpublishenum-skip-method.md)|<span data-ttu-id="4e378-114">Przenosi kursor do przodu w wyliczeniu o określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="4e378-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e378-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e378-115">Remarks</span></span>  
 <span data-ttu-id="4e378-116">Następujące moduły wyliczające pochodzą z `ICorPublishEnum` :</span><span class="sxs-lookup"><span data-stu-id="4e378-116">The following enumerators derive from `ICorPublishEnum`:</span></span>  
  
- [<span data-ttu-id="4e378-117">ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="4e378-117">ICorPublishAppDomainEnum</span></span>](icorpublishappdomainenum-interface.md)  
  
- [<span data-ttu-id="4e378-118">ICorPublishProcessEnum</span><span class="sxs-lookup"><span data-stu-id="4e378-118">ICorPublishProcessEnum</span></span>](icorpublishprocessenum-interface.md)  
  
## <a name="requirements"></a><span data-ttu-id="4e378-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4e378-119">Requirements</span></span>  
 <span data-ttu-id="4e378-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e378-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e378-121">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="4e378-121">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="4e378-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4e378-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e378-123">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e378-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e378-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e378-124">See also</span></span>

- [<span data-ttu-id="4e378-125">CorpubPublish — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="4e378-125">CorpubPublish Coclass</span></span>](corpubpublish-coclass.md)
- [<span data-ttu-id="4e378-126">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4e378-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
